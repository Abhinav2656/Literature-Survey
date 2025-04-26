Paper Title: **Unsupervised Cross-Modality Domain Adaptation of ConvNets for Biomedical Image Segmentations with Adversarial Loss**  
**Authors**: Y. Zhang, Q. Dou, H. Liu, and P. A. Heng  
**Conference**: IJCAI 2018  

---

### 🎯 Objective  
The objective of this paper is to perform **unsupervised adaptation** for medical image segmentation by learning **modality-invariant representations** using a CNN encoder-decoder structure enhanced with **adversarial domain adaptation**, without labeled CT data.

---

### 🧠 Methodologies & Innovations

1. **Adversarial Feature Learning**  
   Introduces a discriminator to distinguish features from source (MRI) and target (CT) domains.

2. **Dual Encoder-Decoder Framework**  
   Uses a common encoder with two decoders - one for segmentation and another for domain classification.

3. **Patch-Level Discriminator**  
   The discriminator operates on extracted features instead of full images, enabling finer domain adaptation.

4. **Unsupervised Adaptation Loss**  
   Adversarial training encourages feature invariance across modalities.

---

### 🧪 Data Preprocessing

1. **Z-Score Normalization**  
   Standardize each scan slice:
   ![Z-Score Normalization](../Images/zscore_normalization.png)

2. **Histogram Matching**  
   Reduces modality shift between CT and MRI images:
   ![Histogram Matching](../Images/histogram_matching.png)

3. **Resizing and Cropping**  
   - Resize all images to 256×256 pixels.  
   - Center-crop to focus on regions of interest.

4. **Data Augmentation**  
   - Random horizontal and vertical flips.  
   - Random rotations (up to ±10 degrees).  
   - Gaussian noise addition.

---

### 🗂️ Dataset Used

- **Source Domain**:  
  Multi-modal Brain Tumor Image Segmentation Benchmark (BraTS) – MRI scans (T1c modality).

- **Target Domain**:  
  MICCAI 2015 Head CT Segmentation Dataset – unlabeled CT scans.

- **Preprocessing Summary**:
  - N4 bias field correction.
  - Skull-stripping using FSL/BET.
  - Intensity normalization.
  - Patch-based cropping for efficient training.

---

### 🏗️ Model Architecture

| Component | Description |
|-----------|-------------|
| Encoder | Extracts modality-invariant features. |
| Decoder | Predicts segmentation masks. |
| Domain Discriminator | Distinguishes feature domain origin (source vs. target). |

- **Loss Functions**:
  - **Cross-Entropy Loss** for segmentation.
  - **Adversarial Loss** for domain confusion.

---

### ⚙️ Training Details

| Parameter | Value |
|-----------|-------|
| Framework | TensorFlow |
| Optimizer | Adam |
| Learning Rate | \( 1 \times 10^{-4} \) |
| Batch Size | 4 |
| Number of Epochs | 100 |
| GPU | Nvidia GTX 1080Ti |

---

### 📈 Evaluation Metrics

| Metric | Purpose |
|--------|---------|
| Dice Similarity Coefficient (DSC) | Measures overlap between predicted and ground truth masks. |
| Hausdorff Distance (HD) | Measures boundary error between segmentations. |
| Domain Classifier Accuracy | Measures success of feature domain confusion. |
| Precision and Recall | Evaluate false positives/negatives. |

---

### 🧩 Challenges Addressed

- Lack of paired MRI-CT data.
- Different tissue contrasts between modalities.
- Generalization to unseen CT images without explicit CT labels.
- Reducing domain shift without altering semantic content.

---

### 📌 Impact & Limitations

✅ **Impact**:
- Enables segmentation of CT images without explicit CT labels.
- Reduces burden of cross-modality manual annotation.
- Provides a template for future cross-modality adaptation work.

❌ **Limitations**:
- Focused mainly on brain datasets (BraTS, MICCAI).
- Sensitive to discriminator training instability.
- Not applicable directly to full 3D volumetric data (slice-based).

---

### 🧬 Architecture Overview

- **Input**: MRI/CT images.
- **Encoder**: Extract modality-invariant features.
- **Decoder**: Produce segmentation mask.
- **Discriminator**: Force encoder to produce indistinguishable features between modalities.
- **Loss**: Combined adversarial and segmentation loss to optimize both tasks simultaneously.

---

### 🕰️ Timeline Summary

| Phase | Duration |
|-------|----------|
| Data Collection & Preprocessing | 1 week |
| Model Building and Setup | 2 weeks |
| Adversarial Training and Fine-tuning | 1.5 weeks |
| Validation, Evaluation & Documentation | 1 week |
