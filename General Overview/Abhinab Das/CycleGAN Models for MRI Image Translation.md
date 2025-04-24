## 🔍 Overview

### 🧠 **Background & Motivation**

Magnetic Resonance Imaging (MRI) is a crucial non-invasive imaging technique used for diagnosing neurological conditions. These scans are performed at various **field strengths** (commonly 1.5T and 3T), which impact image resolution and contrast. However, not all datasets are available at multiple field strengths. There is a growing need to **translate images across these field strengths**, especially when working with scarce or unbalanced medical data.

The problem becomes even more pressing when using Diffusion Tensor Imaging (DTI), a specialized form of MRI used for mapping white matter in the brain. While high-field MRIs (3T and above) offer better resolution, **low-field MRIs (e.g., 1.5T)** are preferred in certain clinical situations due to reduced artifacts. Hence, **generating synthetic scans across field strengths** can aid research and clinical diagnosis without repeated scanning.

---

### 🎯 **Objective**

To **build and evaluate a CycleGAN-based image-to-image translation model** that can:

- Translate MRI images **from 3T to 1.5T and vice versa** using **unpaired datasets**
    
- Serve as a proof-of-concept for **domain translation within a single imaging modality**
    
- Compare the quality of generated images against a baseline **DCGAN** model
    

This project differs from traditional modality translation (e.g., MRI ↔ CT) and instead focuses on **field strength translation** within **neuroimaging data**.

---

## 🛠️ **Techniques and Architecture Used**

### 1. **CycleGAN**

A **Cycle-Consistent Generative Adversarial Network (CycleGAN)** is used for **unpaired image translation**, meaning that images from the two domains (1.5T and 3T) don’t need to be aligned or correspond to the same patient.

#### 🧱 Model Components:

- **Two Generators (G and F)**:
    
    - G: Translates 3T → 1.5T
        
    - F: Translates 1.5T → 3T
        
- **Two Discriminators (Dₓ and Dᵧ)**:
    
    - Used to judge if generated images are indistinguishable from real ones.
        
- **Loss Functions**:
    
    - **Adversarial Loss**: Makes generated images look realistic
        
    - **Cycle Consistency Loss**: Ensures G(F(x)) ≈ x and F(G(y)) ≈ y
        
    - **Identity Loss** (implicitly): Helps stabilize training and retain features when no translation is needed
        

#### 📐 Generator Architecture:

- Encoder-decoder style using **ResNet blocks** (9 residual blocks for transformation)
    
- Uses **instance normalization**, **ReLU**, and **fractional strided convolutions** for upsampling
    

#### 🧮 Discriminator:

- Based on **PatchGAN**, which classifies 70x70 overlapping image patches rather than the whole image
    
- 5-layer CNN with LeakyReLU and instance normalization
    

### 2. **Baseline DCGAN Model**

A traditional Deep Convolutional GAN (DCGAN) was also implemented for comparison.

- Separate DCGANs were trained for 1.5T and 3T images.
    
- Architecture:
    
    - **Generator**: Dense → 3 transpose convolution layers → sigmoid output
        
    - **Discriminator**: 3 convolutional layers → flatten → dense sigmoid classifier
        
- Used for **data augmentation**, not translation.
    

---

## 📊 **Dataset and Preprocessing**

- **3T DTI Dataset**: From University of North Carolina (UNC), 350 axial slices from 35 subjects
    
- **1.5T DTI Dataset**: From OpenNeuro, 160 slices from 16 subjects (2 sessions each)
    
- Images resized to 256×256 pixels
    
- 70% used for training, 30% for testing
    
- **No paired datasets**, making it ideal for CycleGAN application
    

---

## 📈 **Evaluation Metrics**

- **PSNR (Peak Signal-to-Noise Ratio)**: Measures reconstructed image quality
    
- **MAE (Mean Absolute Error)** and **MSE (Mean Squared Error)**: Measure pixel-wise reconstruction accuracy
    
- Evaluated forward (3T→1.5T→3T) and backward (1.5T→3T→1.5T) cycles
    

### 📌 Results:

| Model            | MAE (↓)             | MSE (↓)              | PSNR (↑)         |
| ---------------- | ------------------- | -------------------- | ---------------- |
| CycleGAN 3T→1.5T | 2106.27 ± 1218.37   | 0.00328 ± 0.0032     | 25.69 ± 2.49     |
| CycleGAN 1.5T→3T | **602.27 ± 147.41** | **0.00189 ± 0.0013** | **27.22 ± 0.30** |
| DCGAN 1.5T       | 31907.44 ± 415.85   | 0.24 ± 0.0059        | 6.20 ± 0.11      |
| DCGAN 3T         | 22559.57 ± 1875.35  | 0.14 ± 0.021         | 8.68 ± 0.76      |

- **CycleGAN clearly outperformed DCGAN**
    
- Backward cycle (1.5T→3T→1.5T) was more accurate than forward
    
- DCGAN suffered from **mode collapse** (limited image variety)
    

---

## 🚧 **Research Gaps & Limitations**

1. **Limited Dataset**:
    
    - Small number of images due to lack of open-source datasets at varied field strengths
        
    - Translation performance might improve with more varied and larger datasets
        
2. **No Use of Perceptual or Structural Loss**:
    
    - Only adversarial and reconstruction losses used—**SSIM or perceptual losses** (e.g., VGG) could enhance realism and structure preservation
        
3. **Evaluation Based on Low-Level Metrics Only**:
    
    - No clinical/semantic validation (e.g., segmentation accuracy or expert radiologist review)
        
4. **No Cross-Modality Comparison**:
    
    - The study remains focused only on intra-MRI translation, though it lays a strong foundation for **MRI↔CT** extensions (which matches your project’s goal)
        

---

## ✅ **Strengths & Contributions**

- **Pioneering proof-of-concept** for MRI field-strength translation using unpaired data
    
- Provides a **clean and reproducible CycleGAN pipeline** for intra-modality synthesis
    
- Offers a solid **comparison against a traditional GAN** (DCGAN)
    
- Highlights how **CycleGAN can enhance dataset variability and synthetic image realism**
    

---

## 📘 **Takeaways for the Project**

- The techniques and challenges discussed here map directly to our use case (MRI ↔ CT), especially in terms of:
    
    - **Unpaired image translation**
        
    - **Medical realism preservation**
        
    - **Use of CycleGAN with PatchGAN and ResNet**
        
    - **Need for anatomical structure-preserving loss functions**
        
- This paper could act as a **baseline or cited precedent** when justifying why CycleGAN is suited for cross-modality medical image translation.

---

### 📚 **IEEE Citation**

```copy
C. Czobit and R. Samavi, _"CycleGAN Models for MRI Image Translation,"_ arXiv preprint arXiv:2401.00023v2, Jan. 2024. [Online]. Available: [https://arxiv.org/abs/2401.00023](https://arxiv.org/abs/2401.00023)
```