# 📄 Paper Title: **Cross-Modality Image Translation between CT and MRI using CycleGAN for Improved Organ-at-Risk Delineation**  
**Authors**: J. Wolterink, T. Leiner, M. Viergever, I. Isgum  
**Conference**: IEEE Transactions on Medical Imaging (TMI) 2017  

---

### 🎯 Objective
Develop a CycleGAN-based approach to perform **CT-to-MRI** and **MRI-to-CT** image translation, aimed at improving the delineation of organs at risk (OARs) in radiation therapy planning.

---

### 🧠 Methodologies & Innovations

1. **CycleGAN for Unpaired Image Translation**  
   - Two generators (G_CT→MRI, G_MRI→CT) and two discriminators (D_CT, D_MRI).
   - No need for paired CT and MRI images.

2. **Cycle Consistency Loss**  
   - Enforces \( G_{MRI→CT}(G_{CT→MRI}(CT)) ≈ CT \) and vice versa.

3. **Structural Preservation**  
   - Special loss weights assigned to preserve organ boundaries critical for treatment.

---

### 🧪 Data Preprocessing

1. **Histogram Matching**  
   - Standardizes intensity distributions across modalities.

2. **Rigid Registration**  
   - Aligns CT and MRI spatially to ensure anatomical consistency.

3. **Cropping and Resizing**  
   - Focused on the head-and-neck region.
   - Image size normalized to 256×256.

4. **Data Augmentation**  
   - Random rotations, flipping, elastic deformation.

---

### 🗂️ Dataset Used

- **CT Scans**: Public head-and-neck CT dataset.
- **MRI Scans**: Public head-and-neck MRI dataset.
- **Unpaired Training**: Datasets treated as independent.

---

### 🏗️ Model Architecture

| Component | Description |
|-----------|-------------|
| Generators | Residual networks with skip connections |
| Discriminators | PatchGAN classifiers for realism check |

- **Loss Functions**:
  - **Adversarial Loss**
  - **Cycle Consistency Loss**
  - **Identity Mapping Loss** (Preserving structure)

---

### ⚙️ Training Details

| Parameter | Value |
|-----------|-------|
| Framework | TensorFlow |
| Optimizer | Adam |
| Learning Rate | \( 2 \times 10^{-4} \) |
| Batch Size | 1 |
| Training Epochs | 200 |

---

### 📈 Evaluation Metrics

| Metric | Purpose |
|--------|---------|
| Dice Similarity Coefficient (DSC) | For organ segmentation accuracy |
| SSIM (Structural Similarity) | Structural consistency between real and synthetic images |
| PSNR | Image quality evaluation |

---

### 🧩 Challenges Addressed

- **Lack of Paired Data**  
  - Solved by CycleGAN without needing registered pairs.

- **Structural Integrity**  
  - Ensured through identity and cycle-consistency losses.

---

### 📌 Impact & Limitations

✅ **Impact**:
- Reduced need for CT scans (reducing radiation exposure).
- Enabled more accurate organ delineation using synthetic MRIs.

❌ **Limitations**:
- Minor anatomical distortions still observed occasionally.
- Requires good-quality MRIs for effective learning.

---

### 🧬 Architecture Overview

- CycleGAN with residual blocks.
- Patch-based discriminators.
- Skip connections to retain fine spatial features.

---

### 🕰️ Timeline Summary

| Phase | Duration |
|-------|----------|
| Data Preparation | 2 weeks |
| Model Development | 3 weeks |
| Training | 1 week |
| Evaluation | 1 week |
