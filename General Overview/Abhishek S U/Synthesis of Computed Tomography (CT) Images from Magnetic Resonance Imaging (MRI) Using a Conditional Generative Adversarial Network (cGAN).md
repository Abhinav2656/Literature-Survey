📄 Paper Title: **Synthesis of Computed Tomography (CT) Images from Magnetic Resonance Imaging (MRI) Using a Conditional Generative Adversarial Network (cGAN)**  
**Authors**: D. Nie, L. Trullo, J. Lian, C. Petitjean, S. Ruan, D. Shen, and W. Wang  
**Conference**: MICCAI 2017  

---

### 🎯 Objective
Develop a **Conditional GAN (cGAN)**-based method for synthesizing CT images from MRI in an end-to-end fashion, especially for brain imaging applications. The goal is to preserve **fine anatomical structures** while enabling downstream tasks like radiation therapy planning.

---

### 🧠 Methodologies & Innovations

1. **Conditional GAN Architecture**  
   - Generator takes MRI and noise vector as input, conditioned to produce realistic CT images.
   - Discriminator receives real or fake CTs along with corresponding MRIs.

2. **Voxel-Level Loss Functions**  
   - Pixel-wise L1 loss added to adversarial loss for improving intensity-level accuracy.

3. **Context-Aware Feature Matching**  
   - Encourages structural consistency using intermediate feature activations.

---

### 🧪 Data Preprocessing

1. **Skull Stripping**  
   - Non-brain tissues are removed using brain extraction tool.

2. **Rigid Registration**  
   - MRI volumes aligned to CT using affine transformations.

3. **Intensity Normalization**  
   - MRI intensities rescaled to \([0,1]\); CTs clipped to [-1000, 1000] HU then normalized.

4. **Slicing Strategy**  
   - 3D volumes converted into 2D slices for training due to GPU memory limits.

---

### 🗂️ Dataset Used

- **Paired Brain MRI-CT Dataset**  
  - Collected from a clinical study with ethical approval.
  - 20 subjects used: 15 for training, 5 for testing.

---

### 🏗️ Model Architecture

| Component | Description |
|-----------|-------------|
| Generator | U-Net with skip connections |
| Discriminator | PatchGAN (local patch-based classification) |

- **Loss Functions**:
  - **Adversarial Loss**: Trains generator to fool discriminator.
  - **L1 Loss**: Voxel-wise error between real and generated CTs.
  - **Perceptual Loss**: Ensures high-level structural fidelity.

---

### ⚙️ Training Details

| Parameter | Value |
|-----------|-------|
| Framework | TensorFlow |
| Optimizer | Adam |
| Learning Rate | \( 2 \times 10^{-4} \) |
| Batch Size | 1 |
| Epochs | 100 |

---

### 📈 Evaluation Metrics

| Metric | Purpose |
|--------|---------|
| MAE (Mean Absolute Error) | Intensity-level accuracy |
| PSNR | Image quality |
| SSIM | Structural similarity |

---

### 🧩 Challenges Addressed

- **Sharp Tissue Boundaries**  
  - cGAN with L1 and perceptual losses helps capture sharper edges.

- **Modality Gaps**  
  - Conditional GAN improves learning via modality-aware discriminator.

---

### 📌 Impact & Limitations

✅ **Impact**:
- Enabled accurate CT reconstruction for radiation dose planning using only MRI.
- Demonstrated clear bone-structure synthesis from soft-tissue MRIs.

❌ **Limitations**:
- Limited generalization across datasets due to domain-specific tuning.
- 2D training may not fully capture 3D anatomical context.

---

### 🧬 Architecture Overview

- MRI → Generator (U-Net) → Fake CT  
- Fake CT + MRI → Discriminator → Real/Fake decision  
- L1 + GAN + Perceptual Loss combined for training

---

### 🕰️ Timeline Summary

| Phase | Duration |
|-------|----------|
| Data Preprocessing | 1 week |
| Model Training | 2 weeks |
| Testing & Evaluation | 1 week |
