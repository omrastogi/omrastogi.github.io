---
layout: page
title: LiDAR-IMU Fusion Odometry
description: Point-to-plane ICP fused with IMU preintegration in a 15-state error-state Kalman filter, scored against GPS ground truth on KITTI
img: assets/img/projects/lidar_imu_fusion/thumb.png
github: https://github.com/omrastogi/lidar-imu-fusion-odometry
importance: 7
category: coursework
---

Course project for **EECE 5554 Robotics Sensing & Navigation** (Northeastern, Spring 2026, Group 5). Track a vehicle's position and orientation over time using only onboard sensors, no GPS. Two sensors with opposite failure modes: LiDAR gives accurate geometry but only 10 times a second and is ambiguous in featureless places; the IMU is fast but its errors compound quadratically. The filter combines them.

**One-line version:** ICP measures motion between scans, the IMU fills in the gaps and warm-starts the matching, and an error-state Kalman filter blends them into a single trajectory scored against GPS ground truth.

{% include figure.liquid loading="eager" path="assets/img/projects/lidar_imu_fusion/trajectory_comparison.png" title="Trajectory comparison on KITTI 00, 01, 04" class="img-fluid rounded z-depth-1" %}
<div class="caption">
  LiDAR-only, IMU-only and fused trajectories against OXTS ground truth on KITTI sequences 00 (urban loop), 01 (highway) and 04 (straight road).
</div>

## Pipeline

```
LiDAR frames  ──►  Voxel downsample + normals
                            │
IMU batch     ──►  Preintegration (ΔR, Δv, Δp, bias Jacobians)
                            │
                            ▼
                   EKF Predict  ──►  T_init  ──►  ICP Scan Matching
                            │                            │
                            └────────────── T_icp ───────┘
                                                 │
                                                 ▼
                                         EKF Update  ──►  Fused pose (R, v, p)
```

- **Data layer** (`kitti_loader.py`). Reads a KITTI raw drive: Velodyne scans as binary point clouds, OXTS packets for accelerometer and gyro, and the three calibration files relating the IMU, LiDAR and camera frames. Its main job beyond reading files is time alignment: handing back the IMU samples that fall between any two LiDAR frames with correct per-sample durations.
- **Ground truth** (`oxts_to_poses.py`). Converts OXTS latitude and longitude to local Cartesian meters via a Mercator projection, combines that with roll/pitch/yaw into 4×4 poses, and anchors everything to frame zero so pose[0] is identity.
- **LiDAR half** (`scan_matching_icp.py`). Voxel-downsamples each scan, estimates surface normals, and runs point-to-plane ICP between consecutive frames to recover the relative transform. Chaining those gives a LiDAR-only trajectory. Each scan is preprocessed exactly once by reusing the previous target as the next source.
- **IMU half** (`imu_integrator.py`). Preintegration: accumulates gyro and accelerometer samples between two LiDAR frames into a single rotation, velocity and position delta, while propagating a covariance and Jacobians with respect to the biases so a later bias correction can be applied without re-integrating. The deltas are re-expressed in the LiDAR frame via the extrinsic calibration.
- **Fusion** (`ekf.py`). A 15-state error-state Kalman filter over orientation, velocity, position, gyro bias and accelerometer bias. Per frame: predict from the IMU, hand that prediction to ICP as a warm start, run ICP, fold the ICP result back in as a measurement (Joseph-form covariance update). The prediction makes ICP converge faster and more reliably; ICP in turn corrects the IMU's drift and estimates its biases.
- **Evaluation** (`evaluation_plots.py`). Runs all three variants (LiDAR-only, IMU-only, fused) on the same sequence and plots trajectories, error against time and distance, drift rate, and per-frame pose jumps.

## Results

Final position error against OXTS ground truth:

| Configuration   | Seq 01 (highway, 2.6 km) | Seq 04 (straight, 407 m) |
| --------------- | ------------------------ | ------------------------ |
| ICP only        | 406 m                    | 8.3 m                    |
| EKF (initial)   | 1603 m                   | 183 m                    |
| **EKF (fixed)** | **464 m**                | **12 m**                 |

The first fused run drifted far worse than ICP alone. Two defects were isolated by testing each hypothesis independently and rescoring EKF-only reruns against ground truth:

1. **Absolute-position covariance collapse.** ICP produces a *relative* pose, but the measurement Jacobian mapped it onto the absolute position error state. Every update compressed the position covariance toward the measurement noise and the Kalman gain decayed monotonically, so ICP could no longer correct accumulating IMU velocity and bias error. Fix: floor the position covariance diagonal before each update. A stochastic-cloning or sliding-window formulation is the principled long-term fix.
2. **Wrong SE(3) inverse of the ICP measurement.** The update used `−t` instead of `−Rᵀt`, dropping the rotation. Negligible on straight roads, about 200 m of error on the high-speed highway sequence.

After the fix the fused filter tracks ICP-only closely on both sequences. It does not beat it: the remaining gap is the relative-measurement problem above, which a covariance floor only patches.

## Stack

Python · NumPy · Open3D · Matplotlib · KITTI raw (hosted on [HuggingFace](https://huggingface.co/datasets/omrastogi/lidar_imu_odometry))
