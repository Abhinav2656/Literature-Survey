# 📄 Paper Title: **“Unsupervised Cross-Modality Domain Adaptation of ConvNets for Biomedical Image Segmentations with Adversarial Loss”**  
**Authors**: Y. Zhang, Q. Dou, H. Liu, and P. A. Heng  
**Conference**: IJCAI 2018  
**Link**: [Paper PDF](https://www.ijcai.org/proceedings/2018/0074.pdf)

---

### 🎯 **Objective**  
To perform **unsupervised cross-modality adaptation** for medical image segmentation by learning **modality-invariant representations** using a CNN encoder-decoder structure enhanced with **adversarial domain adaptation**.  
Target: Translate features learned from **MRI** to be applicable on **CT** (and vice versa) for segmentation, without labeled CT data.

---

### 🧠 **Methodologies & Innovations**

- **Adversarial Feature Learning**: Introduces a discriminator to distinguish source (MRI) from target (CT) domain features.
- **Dual Encoder-Decoder Framework**: Only source data is labeled; target domain relies on learned feature alignment.
- **Unsupervised Adaptation Loss**: Forces target domain features to mimic the source domain’s statistical characteristics.
- **Patch-Level Discriminator**: Discriminator works on features, not images, improving generalization.

---

### 🧪 **Data Preprocessing**

#### 1. **Z-Score Normalization**  
Standardizes each scan slice:  
\[
I_{\text{norm}} = \frac{I - \mu}{\sigma}
\]  
Where \( \mu \) and \( \sigma \) are the mean and standard deviation of the slice.

#### 2. **Histogram Matching**  
To reduce modality shift between CT and MRI:  
\[
I_{\text{matched}} = \text{CDF}^{-1}_{\text{ref}}(\text{CDF}_{\text{input}}(I))
\]

#### 3. **Resizing & Cropping**  
All slices are resized to a fixed dimension (e.g., 256×256) and center-cropped.

#### 4. **Data Augmentation**  
Includes flipping, rotation, and Gaussian noise to improve domain generalization.

---

### 🗂️ **Dataset Used**

- **Source**: Multi-modal Brain Tumor Image Segmentation Benchmark (BraTS)
  - MRI modalities used: T1c (contrast-enhanced)
- **Target**: MICCAI 2015 Head CT Segmentation Dataset
- **Preprocessing Details**:
  - N4 bias field correction
  - Skull-stripping using FSL/BET
  - Patch-based training for memory efficiency

---

### 🏗️ **Training Details**

| Parameter | Value |
|----------|-------|
| Framework | TensorFlow |
| Optimizer | Adam |
| Learning Rate | 1e-4 |
| Batch Size | 4 |
| Losses | Cross-entropy (for segmentation), Adversarial loss (feature alignment) |
| Training Time | ~15 hours on Nvidia GTX 1080Ti |

---

### 📈 **Evaluation Metrics**

| Metric | Description |
|--------|-------------|
| Dice Similarity Coefficient (DSC) | Measures overlap between predicted and ground truth masks |
| Hausdorff Distance (HD) | Measures boundary error between segmentation contours |
| Precision/Recall | Standard segmentation metrics to evaluate false positives/negatives |
| Domain Classifier Accuracy | How distinguishable the features are across domains (lower is better) |

---

### 🧩 **Challenges Addressed**

- **No paired data** between MRI and CT scans  
- MRI and CT have vastly different tissue contrasts and artifacts  
- Labeling is available only for MRI → Need to generalize to CT  
- Avoid domain overfitting and improve **generalizability**

---

### 📌 **Impact & Limitations**

#### ✅ Impact:
- Demonstrates how **unlabeled CT scans** can be segmented using only MRI-based labeled training.
- Reduces clinical burden of annotating each modality individually.
- Opens door for low-resource hospitals to use pretrained models cross-modally.

#### ❌ Limitations:
- Fails to explicitly reconstruct synthetic images (no image-to-image translation).
- Evaluation limited to **brain datasets**.
- Sensitive to discriminator overfitting.

---

### 🧬 **Architecture Overview**

![Domain Adaptation Network](https://i.ibb.co/mTnGx7M/domain-adapt.png)

> *Encoder extracts shared features. A discriminator tries to distinguish modality origin. Decoder is supervised only by source domain labels.*

---

### 🕰️ **Timeline Summary**

| Phase | Duration |
|-------|----------|
| Data Collection & Preprocessing | 1 week |
| Network Setup & Pretraining | 2 weeks |
| Domain Adaptation Training | 1.5 weeks |
| Evaluation & Visualization | 1 week |

---
