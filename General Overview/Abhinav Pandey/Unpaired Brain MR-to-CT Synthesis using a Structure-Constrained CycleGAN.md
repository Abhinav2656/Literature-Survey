### 📄 Summary of the Paper

**Title:** _Unpaired Brain MR-to-CT Synthesis using a Structure-Constrained CycleGAN_  
**Authors:** Heran Yang, Jian Sun, Aaron Carass, Can Zhao, Junghoon Lee, Zongben Xu, Jerry Prince  
**Published in:** Proceedings of MICCAI, 2018  
**arXiv:** [1809.04536](https://arxiv.org/abs/1809.04536)

---

### 🔍 Objective

To generate structurally consistent synthetic CT images from unpaired MR images using a **Structure-Constrained CycleGAN**. The work introduces:

- A novel **structure-consistency loss** based on the **Modality Independent Neighborhood Descriptor (MIND)**
- A **position-based slice selection strategy** for better training efficiency and anatomical correspondence

---

### 🧠 Methodologies and Innovations

#### ✅ 1. CycleGAN Backbone:
Two generators (G<sub>CT</sub>, G<sub>MR</sub>) and two discriminators (D<sub>CT</sub>, D<sub>MR</sub>) to learn bidirectional mappings between CT and MR domains using unpaired data.

#### ✅ 2. Structure-Consistency Loss:
Addresses the limitation of conventional CycleGAN where structural fidelity is not enforced.

The **MIND feature** captures self-similarity in non-local patches around each voxel, invariant to modality.

**MIND feature for voxel x:**

<img src="images/figure_1.png" alt="" width="600"/>

Where:
- _Z_ = normalization constant
- _DP_ = patch distance:  
- _V(I, x)_ = local variance:

<img src="images/figure_2.png" alt="" width="600"/>

Final **Structure-Consistency Loss**:

<img src="images/figure_3.png" alt="" width="600"/>

#### ✅ 3. Training Loss:

<img src="images/training_loss.png" alt="Training Loss" width="600"/>


Where:
- \( \lambda_1 = 10 \)
- \( \lambda_2 = 5 \)

#### ✅ 4. Position-Based Slice Selection:
Aligns training slices by anatomical position to improve learning stability:
```
T(i) = \left[ \frac{i \cdot (K_{CT} - 1)}{K_{MR} - 1} \right] + m
```
Where m is a random offset in [−5, 5].

---


### 📊 Experimental Setup and Evaluation

This section outlines the dataset used in the study, how it was prepared, and the metrics used to evaluate the model's performance.

---

#### 🧠 **Dataset Overview**

- The study used **45 unpaired brain MR and CT volumes** collected from clinical routines.
- These datasets likely included different patients for MR and CT, reflecting **real-world clinical limitations** where paired MR-CT volumes are rare due to scheduling, cost, or ethical constraints.
- **Data Split:**
  - **Training set:** 27 subjects
  - **Validation set:** 3 subjects
  - **Test set:** 15 subjects

The choice of using unpaired data makes the approach **more applicable to clinical settings**, where MR and CT scans are often not available for the same patient at the same time or resolution.

---

#### 🔄 **Preprocessing Method**

Preprocessing ensures uniformity in image quality and geometry before training the model. The following steps were carried out:

1. **Slice Extraction from 3D Volumes:**
   - MR and CT scans are 3D volumes. They were converted into **2D axial slices**, as the model operates on 2D data.
   - This approach simplifies training while still capturing useful structural information from each plane.

2. **Image Alignment Strategy - Position-Based Slice Selection (PBS):**
   - Since MR and CT images are unpaired, **PBS** was used to align the anatomical location of slices.
   - This technique selects CT slices that correspond anatomically (by position) to a given MR slice using:
     ```
     T(i) = floor[(i × (K_CT - 1)) / (K_MR - 1)] + m
     ```
     where:
     - *i* is the index of the MR slice,
     - *K_CT*, *K_MR* are the number of slices in the CT and MR volumes, respectively,
     - *m* is a random offset within [–5, +5] to add variability.

3. **Intensity Normalization:**
   - Medical images often have widely varying intensity ranges, especially between modalities like MR and CT.
   - Normalization ensures all images have comparable intensity values, improving GAN stability.

4. **Resizing:**
   - All slices were likely resized (commonly to 256×256) to fit the model architecture and batch processing constraints.

---

#### 📐 **Evaluation Metrics**

To assess image quality and structural preservation, the study employed several standard and domain-specific metrics:

| Metric | Description |
|--------|-------------|
| **MAE (Mean Absolute Error)** | Measures average pixel-wise intensity error between synthesized and real CT |
| **PSNR (Peak Signal-to-Noise Ratio)** | Reflects the overall quality and clarity of the image reconstruction |
| **SSIM (Structural Similarity Index)** | Evaluates image similarity based on structure, contrast, and luminance |
| **SSIM(HG)** | SSIM computed only on **high-gradient regions**, useful for checking **bone structure fidelity** in CT images |

---

#### 🔁 **Comparison Models**

To validate the improvements brought by the proposed structure-constrained CycleGAN, results were compared against:

- **Conventional CycleGAN**  
  Baseline GAN model without structure or slice selection constraints.

- **CycleGAN + PBS**  
  Introduces position-based slice alignment to improve anatomical matching.

- **CycleGAN with Paired Data**  
  Trained with directly aligned MR-CT pairs (ideal but impractical scenario).

- **Proposed Method (Structure-Constrained CycleGAN)**  
  Adds MIND-based structural similarity loss + PBS for best alignment and realism.


#### ⚡ Quantitative Results (Average over 15 test subjects):
| Method             | MAE ↓ | PSNR ↑ | SSIM ↑ | SSIM(HG) ↑ |
|--------------------|---------|----------|------------|---------------|
| CycleGAN           | 150.3   | 23.09    | 0.732      | 0.546         |
| CycleGAN (PBS)     | 147.0   | 23.29    | 0.740      | 0.592         |
| CycleGAN (paired)  | 122.7   | 24.57    | 0.785      | 0.630         |
| **Proposed Method**| **129.0** | **24.15** | **0.779**  | **0.617**     |

- Proposed model significantly outperforms vanilla CycleGAN (p < 0.001)
- Comparable to a CycleGAN trained with paired data

---

### ⛔ Challenges Addressed
- Structural inconsistencies in conventional CycleGAN-generated images
- Lack of paired data availability in clinical scenarios
- Mode collapse from random unaligned training slices

---

### ❓ Challenges Left for Future Work
- Extension to 3D volumetric GANs (this work uses 2D slices)
- Domain adaptation across scanners and populations
- Integration of attention mechanisms or multi-modal input features
- Real-time performance optimization for clinical deployment

---

### 🔬 Contributions and Clinical Impact
- First method to enforce structural similarity using a descriptor (MIND) without ground-truth segmentation
- Introduced simple yet effective training strategy (PBS)
- Can potentially reduce patient CT scans in radiotherapy planning

---

### 📃 Citation (IEEE Format):
```bibtex
H. Yang, J. Sun, A. Carass, C. Zhao, J. Lee, Z. Xu, and J. Prince, “Unpaired Brain MR-to-CT Synthesis using a Structure-Constrained CycleGAN,” in *Proc. MICCAI*, 2018. [Online]. Available: https://arxiv.org/abs/1809.04536
```

---

### 🔍 Useful for:
- Beginners in medical imaging AI
- Researchers working on image synthesis or GANs
- Developers building clinical tools for radiation planning or attenuation correction

