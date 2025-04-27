
### 📄 Summary of the Paper

**Title:** _Unsupervised Medical Image Translation Using Cycle-MedGAN_  
**Authors:** Karim Armanious, Chenming Jiang, Sherif Abdulatif, Thomas Küstner, Sergios Gatidis, Bin Yang  
**Published in:** 2019 European Signal Processing Conference (EUSIPCO)  
**DOI:** [10.23919/EUSIPCO.2019.8902587](https://ieeexplore.ieee.org/document/8902587)

---

### 🔍 Objective

The paper proposes **Cycle-MedGAN**, an unsupervised medical image translation framework, based on CycleGAN, designed to improve perceptual quality without requiring paired datasets. It focuses on reducing blurry translations and enhancing fine structural details using new **non-adversarial cycle losses**.

---

### 🧠 Methodologies and Innovations

#### ✅ 1. Base CycleGAN Framework
Bidirectional unsupervised translation using two generators and two discriminators.

#### ✅ 2. New Non-Adversarial Cycle Losses
- **Cycle-Perceptual Loss:** Reduces perceptual discrepancies between input and cycle-reconstructed images.
- **Cycle-Style Loss:** Preserves texture and style consistency using Gram matrices.

#### ✅ 3. Combined Final Loss
The final optimization includes:
```math
L = L_{adv} + λ_{cP} L_{cPercep} + λ_{cyc} L_{cyc} + λ_{cS} L_{cStyle}
```
Where λ weights balance adversarial, perceptual, cycle-consistency, and style losses.

---

### 🧪 Data Preprocessing and Dataset

#### ⚙️ Dataset Used:
- **PET to CT Translation:**
  - 46 anonymized volunteers (Siemens Biograph mCT PET-CT scanner).
  - 1935 slices (training), 420 slices (validation).

- **MR Motion Artifact Correction:**
  - 17 volunteers (3T MR scanner, Siemens Biograph mMT).
  - 980 slices (training), 105 slices (validation).

#### 🔄 Preprocessing Steps:
- Resampling to **1mm³ isotropic voxel size**.
- Extraction of **2D slices resized to 256×256 pixels**.
- **Random subject shuffling** to ensure unpaired training (no explicit pairing between modalities).

---

### 📊 Experimental Setup and Evaluation

- **Training Details:**
  - Batch Size = 64
  - 50 epochs
  - Adam optimizer
  - Trained using **NVIDIA Titan X GPU**
  - Pre-trained **BiGAN discriminator** used as feature extractor for non-adversarial losses.

- **Metrics Used:**

| Metric | Description |
|:---|:---|
| **PSNR (Peak Signal-to-Noise Ratio)** | Measures ratio between signal strength and noise. Higher is better. |
| **SSIM (Structural Similarity Index)** | Evaluates similarity in structure and luminance. Higher is better. |
| **VIF (Visual Information Fidelity)** | Measures visual information preservation. Higher indicates better quality. |
| **LPIPS (Learned Perceptual Image Patch Similarity)** | Deep feature-based perceptual distance. Lower is better. |

#### 📈 Quantitative Results:

| Task | Method | SSIM ↑ | PSNR ↑ | Other Metrics |
|-----|--------|--------|--------|---------------|
| PET→CT | UNIT | 0.8485 | 20.14 | VIF=0.2057, LPIPS=0.6762 |
| PET→CT | CycleGAN | 0.8963 | 23.35 | VIF=0.3831, LPIPS=0.2561 |
| PET→CT | **Cycle-MedGAN** | **0.9115** | **24.08** | **VIF=0.4275, LPIPS=0.2233** |
| MR Motion Correction | UNIT | 0.6914 | 18.64 | MSE=0.1239, UQI=0.6953 |
| MR Motion Correction | CycleGAN | 0.8011 | 22.39 | MSE=0.3432, UQI=0.3282 |
| MR Motion Correction | **Cycle-MedGAN** | **0.8118** | **22.96** | **MSE=0.3513, UQI=0.3029** |

---

### ⛔ Challenges Addressed

- **Lack of Paired Data:**  
  Enables training using unpaired medical datasets, removing the dependency on difficult-to-obtain co-registered images.

- **Blurriness and Lack of Texture:**  
  Traditional pixel-wise cycle-consistency loss fails to capture human-perceptual quality. The proposed non-adversarial losses improve sharpness and fine details.

---

### ❓ Challenges Left for Future Work

- **Diagnostic Accuracy:**  
  Although Cycle-MedGAN improves visual quality, it may still miss critical diagnostic features, limiting clinical diagnostic use.

- **Extension to 3D and Complex-Valued Data:**  
  Future work planned on **3D volumes** and handling complex MRI phase information to improve motion artifact correction.

- **Expanded Clinical Validation:**  
  More real-world clinical studies and subjective radiologist evaluations are needed.

---

### 🔬 Contributions and Clinical Impact

- Introduces **cycle-perceptual** and **cycle-style losses** for unsupervised medical image translation.
- Outperforms CycleGAN and UNIT in both PET→CT translation and MR artifact correction.
- Advances the field by making high-quality synthetic medical imaging possible without paired datasets.

---

### 📃 Citation (IEEE Format)

```plaintext
K. Armanious, C. Jiang, S. Abdulatif, T. Küstner, S. Gatidis and B. Yang, "Unsupervised Medical Image Translation Using Cycle-MedGAN," 2019 27th European Signal Processing Conference (EUSIPCO), 2019, pp. 1-5, doi: 10.23919/EUSIPCO.2019.8902587.
```

---

### 🔗 Relevance to Our Project

- **Unpaired Training Strategy:**  
  Directly matches our goal of cross-modality synthesis (MRI↔CT) without needing paired datasets.

- **Structural Preservation:**  
  The addition of feature-based perceptual and style losses can significantly improve synthetic CT quality from MR images.

- **Model Architecture:**  
  Simple extensions over CycleGAN (no radical new architecture) make it feasible to integrate similar ideas into our system.
