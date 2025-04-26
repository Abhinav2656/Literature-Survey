
## 📘 Paper Summary

**Title**: _Diffusion Bridge Models for 3D Medical Image Translation_
**Authors**: Shaorong Zhang, Tamoghna Chattopadhyay, Sophia I. Thomopoulos, Jose-Luis Ambite, Paul M. Thompson, Greg Ver Steeg  
**Institutions**: University of California Riverside, Imaging Genetics Center (USC), Information Sciences Institute (USC)  
**Published**: April 2025 (arXiv:2504.15267v1)

---

### **1. Motivation**

- DTI provides crucial information about **brain microstructure** (white matter pathways) but is costly and time-consuming to acquire.
    
- The aim is to **generate synthetic DTI (FA maps)** from widely available **T1-weighted MRI** images to reduce scanning time, cost, and patient discomfort.
    
- Traditional approaches (GANs, VAEs) face issues like **mode collapse** and **blurriness**, motivating the use of **diffusion models**.
    

---

### **2. Methodology**

#### **Diffusion Bridge Models**

- Instead of learning a mapping from noise to data (as in DDPMs), this model learns a **direct conditional transition between source and target modalities**.
    
- A **bridge process** interpolates between the source (T1) and target (DTI) domains using a **Gaussian transition kernel**.
    
- Uses both **ODE and SDE samplers** to control deterministic vs. stochastic translation.
    

#### **Architecture**

- **3D UNet** based on ADM (denoising UNet for diffusion models) is used for the translation task.
    
- **3D CNN** is employed for **downstream evaluations** (sex classification and Alzheimer's Disease classification).
    

---

### **3. Dataset and Preprocessing**

- **ADNI dataset** with 1114 subjects, including healthy controls, MCI, and AD patients.
    
- All images are normalized and resampled to **128×128×128**.
    
- Data split into **training (70%)**, **validation (15%)**, and **testing (15%)**.
    

---

### **4. Evaluation Metrics**

- **MS-SSIM** (Multi-Scale Structural Similarity Index): Measures perceptual similarity.
    
- **PSNR** (Peak Signal-to-Noise Ratio): Pixel-level similarity.
    
- **MMD** (Maximum Mean Discrepancy): Distributional similarity.
    

#### **Results**

- High MS-SSIM (~0.9+), PSNR (>30 dB), and low MMD (<0.005) show strong fidelity.
    
- **ODE samplers** yield reproducible but slightly less sharp results than **SDE**.
    

---

### **5. Downstream Task Validation**

- Classification tasks performed using real and synthetic images:
    
    - **AD Classification**: Synthetic T1 and FA images perform comparably to real ones.
        
    - **Sex Classification**: Slight performance drop in synthetic FA images indicates that **some fine anatomical features** might be harder to preserve.
        
- Notably, **synthetic T1 from FA outperforms real FA**, suggesting enhanced structural representation.
    

---

### **6. Key Takeaways**

- **First use of diffusion bridge models for 3D neuroimaging modality translation**.
    
- Offers **anatomically consistent** and **diagnostically useful** image synthesis.
    
- Provides potential for **clinical decision support**, especially in resource-constrained settings where full imaging modalities are not always available.
    

---

### **7. Limitations & Future Work**

- Limited dataset size (780 training pairs) affects generalization in rare conditions.
    
- Plans to extend model to more **complex DTI representations** (e.g., full tensors), **other modalities** (e.g., pan-contrast MRI), and **other pathologies**.
    

---

## 🧠 How This Can Influence Your Project

- You can explore **Diffusion Bridge Models** as an alternative or complementary method to CycleGANs.
    
- Incorporate **MS-SSIM, MMD**, and **clinical task evaluations** into your own validation pipeline.
    
- Study **bridge SDE/ODE sampling** dynamics for **controllable synthesis**.
    
- Apply the model design for MRI-to-CT or vice versa using **unpaired data**.
    

---

## 📌 IEEE Citation

```copy
S. Zhang, T. Chattopadhyay, S. I. Thomopoulos, J.-L. Ambite, P. M. Thompson, and G. Ver Steeg, “Diffusion Bridge Models for 3D Medical Image Translation,” _arXiv preprint arXiv:2504.15267_, Apr. 2025. [Online]. Available: [https://arxiv.org/abs/2504.15267](https://arxiv.org/abs/2504.15267)
```
