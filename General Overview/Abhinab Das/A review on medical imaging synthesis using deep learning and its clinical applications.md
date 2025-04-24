## 🧠 Descriptive Overview of the Paper

### 📌 Title:

**A review on medical imaging synthesis using deep learning and its clinical applications**

### 🧑‍⚕️ Authors:

Tonghe Wang, Yang Lei, Yabo Fu, Jacob F. Wynne, Walter J. Curran, Tian Liu, Xiaofeng Yang

### 🧾 Publication:

_Journal of Applied Clinical Medical Physics_, 2021 | DOI: 10.1002/acm2.13121

---

## 🎯 Main Focus of the Paper:

This review consolidates over 100 deep learning-based studies on **medical image synthesis** and classifies them based on:

- **Imaging modality pairs** (e.g., MRI → CT, CT → MRI, PET → CT)
    
- **Architectural methods** (e.g., U-Net, GANs)
    
- **Clinical application areas** (e.g., radiation therapy, PET attenuation correction, image registration)
    

The paper places special emphasis on **inter-modality** synthesis (e.g., MRI to CT), which is directly relevant to your project.

---

## 🧬 Deep Learning Techniques Discussed

The paper classifies the reviewed works into **three primary architectural categories**, each increasing in complexity:

### 1. **Autoencoders (AEs):**

- Act as the basic building block of other architectures.
    
- Encoder compresses input features; decoder reconstructs the output.
    
- Variants like **ResNet** (residual connections) help in retaining fine features.
    
- Useful for simpler tasks or as components in larger models.
    

---

### 2. **U-Net Architecture:**

- Widely used in medical image translation and segmentation.
    
- Composed of an encoder-decoder with **skip connections** to preserve spatial features.
    
- Variants discussed:
    
    - **Multi-scale input** (T1, T2, FLAIR)
        
    - **Self-attention** and **Residual Shortcuts** to reduce noise
        
    - **Instance normalization** for small batch sizes
        
    - **Dropout and PReLU** for generalization and adaptive activation
        
- Common loss functions:
    
    - L1/L2 loss (MAE, MSE)
        
    - Gradient difference
        
    - Laplacian and perceptual loss
        
    - Mutual information for registration-agnostic synthesis
        

---

### 3. **Generative Adversarial Networks (GANs):**

- GANs include a **generator** (synthesizes the target modality) and a **discriminator** (distinguishes real from fake).
    
- **CycleGAN** is highly highlighted due to:
    
    - Ability to train on **unpaired data**
        
    - Use of **cycle consistency loss** to preserve anatomical structure
        
- Variants include:
    
    - **Conditional GANs (cGANs)**: Generator & Discriminator are conditioned on input images
        
    - **Wasserstein GANs**: Better gradient flow, less mode collapse
        
    - **Feature matching and perceptual losses** to improve realism
        
- Losses used:
    
    - Adversarial loss
        
    - Cycle consistency loss
        
    - Identity loss (especially helpful when input ≈ output)
        
    - Structural similarity metrics
        

---

## 🏥 Clinical Application Areas Reviewed

### 1. **MRI-to-CT Synthesis:**

- Most common task; used for:
    
    - **Radiation therapy planning**: Avoid CT scan, use MRI-only workflows
        
    - **PET attenuation correction**: Use synthetic CT for photon attenuation mapping
        
    - **Multimodal registration**: Convert MRI to CT to simplify registration
        
- Accuracy metrics:
    
    - **MAE** ranges from 30–70 HU for soft tissues; >100 HU for bone/air due to poor MR contrast
        
    - **CycleGAN** significantly improves bone boundary sharpness over U-Net and GAN
        
    - Real-world clinical usage includes **proton therapy** and **dose map accuracy**
        

---

### 2. **CT/CBCT-to-MRI:**

- Used to generate synthetic MR for better **soft tissue segmentation** or **tumor visibility**
    
- Example: Using synthetic MR to aid prostate segmentation from low-contrast CBCT images
    

---

### 3. **CBCT-to-CT:**

- Used in **adaptive radiation therapy** to improve CBCT image quality
    
- Addresses:
    
    - Artifacts (cupping, streaking)
        
    - Incorrect Hounsfield units (HU)
        
- Techniques:
    
    - GANs and U-Nets in both **projection** and **image domains**
        
    - Synthetic CT yields better dose calculations and visual similarity
        

---

### 4. **PET-to-CT and vice versa:**

- Deep learning helps generate high-quality CT from low-dose or noisy PET scans
    
- Used for **attenuation correction** in PET/MR and PET-only systems
    

---

## 🧪 Metrics and Evaluation Used

- **Image Quality Metrics**:
    
    - MAE (Mean Absolute Error)
        
    - SSIM (Structural Similarity Index)
        
    - PSNR (Peak Signal-to-Noise Ratio)
        
    - Dice Similarity Coefficient (for segmentation accuracy)
        
- **Clinical Metrics**:
    
    - Dose Volume Histogram (DVH) for radiation planning
        
    - PET quantification bias
        
    - Landmark registration errors
        
    - Gamma passing rates in therapy planning
        

---

## 🔍 Research Gaps Identified

1. **Anatomical Detail Preservation:**
    
    - Small features like bones, tumors, and air pockets are hard to synthesize with high fidelity.
        
    - Most methods bias toward soft tissue due to imbalance in training data.
        
2. **Generalization Across Scanners:**
    
    - Many models trained on one MRI/CT scanner do not generalize well across different hardware or sequences.
        
3. **Lack of Unpaired Data Utilization:**
    
    - Though CycleGANs allow unpaired training, most studies still rely on registered paired datasets.
        
4. **Limited Clinical Validation:**
    
    - Very few studies include expert radiologist evaluation or multi-center clinical testing.
        
5. **Registration Errors Affecting Training:**
    
    - MR and CT images are often misaligned.
        
    - Pixel-wise loss functions in GANs are sensitive to this misalignment unless replaced with perceptual or mutual information-based losses.
        
6. **Sequence and Protocol Dependence:**
    
    - Synthesis quality heavily depends on the MRI protocol (T1 vs T2 vs Dixon vs UTE), yet the ideal protocol is not conclusively established.
        

---

## 🚀 Opportunities for Improvement

- Use **multi-sequence or multi-modal input** (e.g., T1 + T2 + Dixon)
    
- Adopt **attention-based mechanisms** to retain important features
    
- Implement **domain adaptation** to improve cross-scanner/generalizability
    
- Use **unsupervised or semi-supervised training** with unpaired datasets
    
- Combine **perceptual, SSIM, and mutual information losses** for robustness
    
- Validate with **clinical trials** or expert annotations for deployment
    

---

## ✅ Relevance to our Project

Our project on **MRI ↔ CT synthesis using CycleGAN** directly aligns with this paper’s core subject. The paper:

- Validates your approach of using **CycleGAN** for unpaired synthesis.
    
- Emphasizes the **need for anatomical preservation**, matching your inclusion of SSIM loss.
    
- Justifies using **U-Net generators**, **PatchGAN discriminators**, and **structural/identity losses**.
    
- Confirms that the **clinical motivation (reducing radiation, cost, scan time)** is both current and impactful.

---

### 📚 IEEE Citation:

```copy
T. Wang, Y. Lei, Y. Fu, J. F. Wynne, W. J. Curran, T. Liu, and X. Yang, “A review on medical imaging synthesis using deep learning and its clinical applications,” _J. Appl. Clin. Med. Phys._, vol. 22, no. 1, pp. 11–36, Jan. 2021, doi: 10.1002/acm2.13121.
```