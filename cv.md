# Om Rastogi

MS in Artificial Intelligence, Northeastern University, Boston, MA.

- Website: https://omrastogi.github.io/
- Email: rastogi.o@northeastern.edu
- GitHub: https://github.com/omrastogi
- LinkedIn: https://www.linkedin.com/in/om-rastogi-a886b4b2
- Google Scholar: https://scholar.google.com/citations?user=BSiwOiMAAAAJ
- CV (PDF): https://omrastogi.github.io/assets/pdf/resume.pdf

## Summary

Om Rastogi is an MS student in Artificial Intelligence at Northeastern University, Khoury College of Computer Sciences. Om works in the Augmented Cognition Lab, advised by Prof. Sarah Ostadabbas. Om's research interests are multimodal LLMs, video understanding, computer vision, and diffusion-based generative models. Om is seeking Summer 2027 research and engineering internships and full-time roles.

## Education

### Northeastern University, Boston, MA

- Master of Science in Artificial Intelligence, Sep 2025 to Aug 2027.
- GPA: 3.6/4.0.
- Khoury College of Computer Sciences.
- Affiliated with the Augmented Cognition Lab, advised by Prof. Sarah Ostadabbas.

### JSS Academy of Technical Education, Noida, India

- Bachelor of Technology in Electronics and Communication Engineering, Aug 2017 to Jul 2021.
- Score: 71%.
- Creative Head at Quanta JSS. Member of EDC.

## Research

### AdShot: A Benchmark for Advertisement Video Clipping with Multimodal LLMs

- Augmented Cognition Lab, Northeastern University. Second author.
- AdShot evaluates multimodal LLMs on shortening a 30-second ad to a 15-second cut while preserving brand messaging and narrative coherence.
- The benchmark has 823 video pairs across 194 brands.
- Om built the inference pipeline for MLLM video clipping evaluation.
- Om designed the evaluation harness, with automated scoring of temporal coherence, brand retention, and narrative quality.
- Om built AdNotator, the human annotation system used to construct the ground-truth clipping decisions.
- Accepted at the NeurIPS 2026 Datasets and Benchmarks Track.
- Project page: https://omrastogi.github.io/projects/1_adshot/

### MotionBlind: Probing the Illusion of Motion Understanding in Video-LLMs

- Augmented Cognition Lab, Northeastern University. Co-author (7th of 10 authors).
- MotionBlind is a contrastive, minimal-pairs benchmark of self-recorded clip pairs that differ only in motion (speed, magnitude, direction).
- Open Video-LLMs score near the 6.25% chance floor. Only Gemini 3.1 Pro clears the benchmark overall.
- Under review at the NeurIPS 2026 Workshop on World Models in Physical AI.
- Project page: https://omrastogi.github.io/projects/motionblind/
- Code: https://github.com/ostadabbas/MotionBlind

### DepthDiT: Diffusion Transformer for Monocular Depth Estimation

- Vision and AI Lab, Indian Institute of Science (IISc), Bengaluru, Jan 2024 to Feb 2025.
- Om trained DepthDiT, a Diffusion Transformer for monocular depth estimation, adapting PixArt-Alpha and PixArt-Sigma backbones.
- The best checkpoint reached AbsRel 0.107 and δ1 0.88 at 40k steps.
- Om built an automated pipeline to curate and QA 30,000 MatrixCity images for depth model training.
- Om designed a masked diffusion loss for reflective surfaces and implemented DreamBooth and RealFill-inspired inpainting workflows.
- Project page: https://omrastogi.github.io/projects/2_depthdit/
- Code: https://github.com/omrastogi/DepthDiT

### Robin: In-House Voice Assistant for AI-CARING

- PARCS Lab, Northeastern University.
- Om built the full system: the server speech cascade (Parakeet speech-to-text, LLM, Kokoro text-to-speech), the tablet app, and the WebSocket protocol between them.
- Om trained and benchmarked the custom "Hey Robin" wake word. The shipped model reached real-voice AUC 0.954, precision 0.92, and recall 0.68.
- Project page: https://omrastogi.github.io/projects/robin/

### GVHMR Multi-Person Extension

- Augmented Cognition Lab, Northeastern University.
- Om is extending GVHMR to multi-person scenarios using scene detection, Visual Odometry patching, SMPL mesh overlay rendering, and YOLO tracking on the Northeastern Discovery cluster (SLURM).
- The work supports an IARPA MOVES pre-proposal.
- Project page: https://omrastogi.github.io/projects/4_gvhmr/

### Transfer Learning for Cryo-ET Classification

- Research Collaborator, Carnegie Mellon University, remote, Oct 2023 to Feb 2024.
- Om evaluated transfer learning for 3D cryo-ET classification using MedicalNet and ModelNet40-pretrained models.
- Om analyzed pretrained representations with t-SNE to assess cross-domain transferability to cryo-ET.
- Om converted 3D cryo-ET volumes into point-cloud representations for comparison against voxel-based pipelines.

## Experience

### Graduate Research Assistant, Augmented Cognition Lab, Northeastern University

- Boston, MA. Sep 2025 to present.
- Research on multimodal ML, video understanding, and human motion estimation, under the supervision of Prof. Sarah Ostadabbas.
- Co-authored AdShot, a benchmark for advertisement video clipping with multimodal LLMs, accepted at NeurIPS 2026 Datasets & Benchmarks track.
- Extending GVHMR to multi-person scenarios using scene detection, Visual Odometry patching, SMPL mesh overlay rendering, and YOLO tracking on Northeastern Discovery cluster (SLURM).
- Supporting IARPA MOVES pre-proposal at the Augmented Cognition Lab.

### Research Engineer, Dashtoon

- Bengaluru, India. Mar 2025 to Aug 2025.
- Trained and shipped Flux LoRA adapters for 20+ characters across 8 animation styles; validated at 2048 resolution with FP16, batching, and caching optimizations.
- Integrated Hidream-l1 (MoE) into animated character pipeline; improved prompt alignment and output smoothness at 2048 resolution.
- Curated 10,000+ image Bollywood dataset from 100+ movies via automated extraction pipeline to reduce regional bias in generation.
- Evaluated Google Veo 2 (early access) for character animation; partnered with GCP team to integrate workflow into Frameo AI platform.

### Project Associate, Vision and AI Lab, Indian Institute of Science (IISc)

- Bengaluru, India. Jan 2024 to Feb 2025.
- Trained DepthDiT, a Diffusion Transformer for monocular depth estimation, adapting PixArt-Alpha and PixArt-Sigma backbones; best checkpoint AbsRel 0.107, δ1 0.88 at 40k steps.
- Built automated pipeline to curate and QA 30,000 MatrixCity images for depth model training.
- Designed masked diffusion loss for reflective surfaces; implemented DreamBooth and RealFill-inspired inpainting workflows.

### Senior Research Engineer (Founding Member), Menmitsu Private Limited (Collablens)

- Gurugram, India. Dec 2022 to Jan 2024.
- ITC Freight Damage Mitigation: deployed YOLO-based truck-loading monitoring achieving 70% rough-handling detection accuracy with <5% false positives; led integration of 3 intelligent modules operating in near real-time.
- Smartivity Defect Detection: achieved 97% accuracy on missing-part detection, reducing inspection time from 10 to 2 seconds (5x speedup); built millimeter-precision homography-based deviation detection system.

### Data Scientist, EZ Works

- Gurugram, India. Jul 2021 to Dec 2022.
- Finetuned Neural Machine Translation models (Arabic-English) exceeding 50 BLEU score; deployed with ONNX-optimized beam search for faster inference.
- Built BERT-based translation memory with custom batch cosine similarity achieving 10x retrieval speedup.
- Implemented LCNN for wireframe and tabular detection in PPT; built document segmentation for image-based documents.
- Built EZ Flip chart/diagram conversion modules with 100% error-free output at 3x speed improvement.

### Machine Learning Engineer (Intern), CyberCure Technologies

- India. Dec 2020 to Jun 2021.
- Built LSTM-based demand forecasting for 200+ products across state/territory/beat/shop-owner hierarchy; 90% accuracy on frequently selling products.
- Added convolutional models to mitigate exogenous correlation, improving accuracy and reducing training/inference time by 2x.
- Designed and deployed analytics dashboard for predictions and demand analysis.

### Python Developer (Intern), Arcturus Business Solutions

- Noida, India. Sep 2019 to Jan 2020.
- Upgraded GUI for Intelligent Surveillance Solution using Python PyQt5 and SQL.
- Added new features and incorporated statistical dashboard into existing system.

### Intern, Central Electronics Limited

- Ghaziabad, India. Jun 2018 to Jul 2018.
- Quality check in System Production Department; training in Digital Axle Counter for Indian Railways, Solar Panels, and Microwave Electronics.

## Publications

1. Wen Xie, Om Rastogi, Sai Siddhartha Vivek Dhir Rangoju, Gijs Overgoor, Yakov Bart, Sarah Ostadabbas. "AdShot: A Benchmark for Advertisement Video Clipping with Multimodal LLMs." NeurIPS 2026 Datasets and Benchmarks Track, 2026.
2. Dhairya Bhatia, Bishoy Galoaa, Oliver Fritsche, Shahid Kamal, Muhammad Obaidullah Abdul Salam, Umer Saleem, Om Rastogi, Frania Felix Chettiar, Nesli Erdoğmuş, Sarah Ostadabbas. "MotionBlind: Probing the Illusion of Motion Understanding in Video-LLMs." Under review, NeurIPS 2026 Workshop on World Models in Physical AI, 2026.
3. Om Rastogi. "Enhancing Pretrained Machine Translation Models: A Literature Review." Preprint, Zenodo, 2025. DOI: 10.5281/zenodo.14649605.
4. Om Rastogi and others. "Color Masking Method for Variable Luminosity in Videos with Application in Lane Detection Systems." Proceedings of International Conference on Machine Intelligence and Data Science Applications, Springer, 2021. DOI: 10.1007/978-981-33-4087-9_24.

## Skills

- Machine Learning and AI: PyTorch, Diffusion Models, Transformers, LoRA, Flux, DiT, Computer Vision, Multimodal LLMs, Depth Estimation, YOLO, NMT, BERT.
- Infrastructure and Deployment: AWS, GCP, Docker, SLURM, ONNX, FastAPI, LangGraph, ChromaDB, Railway, Vercel.
- Programming: Python, SQL, PyQt5, React.
