
### 📄 Summary of the Paper

**Title:** _Enhanced Synthetic MRI Generation from CT Scans using CycleGAN with Feature Extraction_  
**Authors:** Saba Nikbakhsh, Lachin Naghashyar, Morteza Valizadeh, Mehdi Chehel Amirani  
**Published in:** (Preprint, 2023)  
**Link:** (No direct link, referenced from uploaded PDF)

---

### 🔍 Objective

The paper proposes **CycleGAN+FE**, an enhanced CycleGAN model that integrates a **Feature Extractor** to improve synthetic MRI image generation from CT scans. The goal is to better retain soft-tissue details and reduce mode collapse, addressing the high cost and longer acquisition time of MRI imaging in radiotherapy planning.

---

### 🧠 Methodologies and Innovations

#### 1. CycleGAN+Feature Extractor (CycleGAN+FE)
Enhances CycleGAN by adding a feature extractor (modified PatchGAN) to better capture anatomical details.

#### 2. Feature Vector Loss
Introduced a new loss based on Mean Squared Error (MSE) between feature vectors extracted from real and synthetic images.

#### 3. Dual-Phase Training
Two-phase updating strategy: first updates G_{MR} (CT→MRI generator), then G_{CT} (MRI→CT generator), ensuring balanced learning.

#### 4. Loss Functions
- **Adversarial Loss** for realism
- **Identity Loss** for preserving input when translating to itself
- **Cycle Consistency Loss** for ensuring forward-backward reconstruction
- **Feature Extractor Loss** for better structural consistency

Final total loss:
```math
L_{GMR} = L_{GAN} + αL_{identity} + βL_{cycle} + γL_{feature}
```
Where:  
α = 5, β = 9.99, γ = 0.01

---

### 🧪 Data Preprocessing and Dataset

#### ⚙️ Dataset Used:
-The authors used the **Gold Atlas Project Dataset**, consisting of paired CT and MRI scans collected from **19 male patients** focusing on the **pelvic region**.

-These scans were specifically chosen because of their relevance to radiotherapy treatment planning, where accurate organ representation is crucial.

-Having paired CT-MRI data allows direct supervised learning and evaluation for structural and intensity fidelity during image synthesis.

#### 🔄 Preprocessing Steps:
- **Normalization:** CT and MRI intensity values were first normalized to a [–1, 1] range. This step ensures that all images fed into the network have comparable scales, which stabilizes GAN training.
- **Resizing:** Each 2D slice was resized to **256×256** pixels to fit the input requirements of the CycleGAN-based model, and to reduce memory consumption during training.
- **Data Augmentation:**
  - Random cropping : To simulate slight positional shifts.
  - Horizontal flipping: With a 50% chance to simulate anatomical variation.
  - Small rotations (–5° to +5°) to make model rotation-invariant.
- Final dataset: **2884 paired CT-MRI slices** ready for training and testing.

---

### 📊 Experimental Setup and Evaluation

- **Training Details:**
  - Trained on **NVIDIA RTX 3070 GPU**
  - **200 epochs**, batch size = 1
  - **Adam optimizer**, learning rate = 0.0002 (halved after 100 epochs)
  - Used an **Image Pool** of 50 past generated images to stabilize GAN training

- **Metrics Used:**
  | **Metric** | **Description** |
  |:-----------|:----------------|
  | **MAE (Mean Absolute Error)** | Measures the average absolute difference between predicted and ground truth pixel values. Lower is better. |
  | **MSE (Mean Squared Error)** | Measures the average squared difference between predicted and true images. Punishes larger errors more. Lower is better. |
  | **PSNR (Peak Signal-to-Noise Ratio)** | Measures the ratio between maximum possible signal power and distortion. Higher PSNR indicates better image quality. |
  | **SSIM (Structural Similarity Index Measure)** | Evaluates the perceived quality by comparing structural information, contrast, and luminance between two images. Higher SSIM means more realistic and structure-preserving output. |


#### 📈 Quantitative Results:

| Network               | MAE ↓  | MSE ↓  | PSNR ↑  | SSIM ↑ |
|------------------------|--------|--------|---------|--------|
| UNet                   | 14.43  | 770.30 | 20.19   | 0.66   |
| Pix2Pix                | 13.15  | 657.55 | 20.83   | 0.66   |
| CycleGAN (Unpaired)    | 13.09  | 648.94 | 20.7    | 0.62   |
| CycleGAN+FE (Unpaired) | 13.2   | 631.51 | 20.85   | 0.62   |
| **CycleGAN+FE (Paired)** | **12.26** | **549.19** | **21.43** | **0.62** |

---

### ⛔ Challenges Addressed

- **Mode Collapse:**  
  Feature extractor and cycle-consistency losses reduce the risk of repetitive or identical outputs during training.

- **Low Detail Preservation:**  
  Feature loss ensures that fine anatomical details like tissue edges are better captured compared to standard CycleGAN.

- **Paired Data Dependency:**  
  Although paired data improves performance, the model still performs competitively on unpaired datasets, which is important in clinical practice.

---

### ❓ Challenges Left for Future Work

- **Expand Dataset Size:**  
  The model was trained on only 19 subjects. A larger dataset would help validate its generalization across diverse anatomies.

- **3D Volumetric Learning:**  
  Currently trained slice-by-slice (2D). Moving to full 3D volume translation would preserve continuity between slices.

- **Dynamic Loss Weighting:**  
  Gradually adjusting the feature loss weight γ during training could optimize both texture realism and structure retention.

---

### 🔬 Contributions and Clinical Impact

- First study to combine a **feature extractor** with CycleGAN for CT-to-MRI synthesis.
- Outperforms traditional CycleGAN, UNet, and Pix2Pix baselines.
- Could help **reduce dependency on expensive MRI scans**, especially in radiotherapy planning, saving cost and patient time.

---

### 📃 Citation (IEEE Format)
```
S. Nikbakhsh, L. Naghashyar, M. Valizadeh, and M. C. Amirani, "Enhanced Synthetic MRI Generation from CT Scans using CycleGAN with Feature Extraction," Preprint, 2023.

```

---

### 🔗 Relevance to Our Project

- **Feature Extractor Innovation:**  
  Incorporating feature-based loss can further enhance the structural realism of our synthetic CT outputs from MRI inputs.

- **CycleGAN Enhancement:**  
  Demonstrates how augmenting CycleGAN (with minimal architecture changes) can yield strong results even on small, clinical datasets.

- **Training Strategy Improvement:**  
  Dual-phase updating and the idea of separately optimizing both directions (CT→MRI and MRI→CT) could improve stability and quality in our project.
