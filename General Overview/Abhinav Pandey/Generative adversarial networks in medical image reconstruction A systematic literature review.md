## 📄 Summary of the Paper: _Generative Adversarial Networks in Medical Image Reconstruction: A Systematic Literature Review_

**Title:** _Generative adversarial networks in medical image reconstruction: A systematic literature review_  
**Authors:** Jabbar Hussain, Magnus Båth, Jonas Ivarsson  
**Published in:** *Computers in Biology and Medicine*, vol. 191, 2025  
**DOI:** [10.1016/j.compbiomed.2025.110094](https://doi.org/10.1016/j.compbiomed.2025.110094)

---

### 🔍 Objective

This systematic review evaluates the application of **Generative Adversarial Networks (GANs)** for **medical image reconstruction**. It aims to identify trends, use cases, limitations, and opportunities across a wide range of organs and imaging modalities, providing a detailed picture of how GANs enhance clinical imaging through synthesis, artifact removal, and modality translation.

---

### 🧠 Methodologies and Innovations

#### ✅ 1. Systematic Review Protocol
- Explores **175 GAN implementations** using:
  - 122 datasets
  - 89 evaluation metrics
  - 10 image reconstruction tasks
  - 31 organs
  - 18 modalities
- Structured review via ACM Digital Library and similar scientific repositories.

#### ✅ 2. Core Applications
- **Reconstruction from limited data:** Enhances quality in low-dose or under-sampled CT/MRI.
- **Synthetic image generation:** Produces realistic images to augment datasets.
- **Artifact removal:** Eliminates motion blur and noise for clarity.
- **Cross-modality translation:** Converts images across modalities like MRI ↔ CT for diagnostic synergy.

---

### 🧪 Data Preprocessing and Datasets

#### ⚙️ Datasets Used
- Public (e.g., NIH, BraTS) and institutional datasets.
- Covers **MRI, CT, PET, ultrasound, and X-ray**.

#### 🔄 Preprocessing
- Uniform **resizing and normalization**.
- **Data augmentation** to expand training data and prevent overfitting.

---

### 📊 Experimental Setup

- GANs tuned with varied **network and batch sizes**.
- Use of **custom loss functions**: perceptual, adversarial, and SSIM/MAE-based.

---

### 📈 Results

- GANs significantly improve **PSNR, SSIM, MAE** across applications.
- High success in tasks like **tumor segmentation**, **image completion**, and **noise suppression**.
- Promising applications in **low-data clinical environments**.

---

### ⛔ Challenges Addressed

- **Sparse-view/missing data**: Reconstructs full-quality images from partial inputs.
- **Noise/artifacts**: Removes imaging imperfections to aid diagnoses.
- **Unpaired data usage**: Enabled by CycleGAN, etc., where direct mappings are unavailable.

---

### ❓ Challenges Left for Future Work

- **Stability**: GANs still suffer from convergence issues.
- **Data demands**: High-quality, diverse training sets remain critical.
- **Ethical barriers**: Calls for transparency and interpretability in clinical GAN models.

---

### 🔬 Contributions and Clinical Impact

- Provides a **foundation for future GAN research** in imaging.
- Highlights key architectural decisions for real-world medical imaging challenges.
- Stresses GANs' role in **automated, accurate, and scalable diagnosis**.

---

### 📌 Relevance to the Project

This review is highly relevant for your **T1W-to-T2W translation project using CycleGAN**. It:
- Validates **cross-modality generation** as a growing field.
- Supports the use of **unpaired learning methods**.
- Offers **design and training recommendations** specific to healthcare.
- Reinforces the clinical value of image quality metrics like **SSIM** and **PSNR**.

---

### 📃 Citation (IEEE Format)

J. Hussain, M. Båth, and J. Ivarsson, “Generative adversarial networks in medical image reconstruction: A systematic literature review,” *Comput. Biol. Med.*, vol. 191, p. 110094, 2025, doi: [10.1016/j.compbiomed.2025.110094](https://doi.org/10.1016/j.compbiomed.2025.110094).
