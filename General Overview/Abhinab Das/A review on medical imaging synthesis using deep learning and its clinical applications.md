
### 📄 Summary of the Paper

**Title:** _A review on medical imaging synthesis using deep learning and its clinical applications_  
**Authors:** Tonghe Wang, Yang Lei, Yabo Fu, Jacob F. Wynne, Walter J. Curran, Tian Liu, Xiaofeng Yang  
**Published in:** _Journal of Applied Clinical Medical Physics_, 2021  
**DOI:** 10.1002/acm2.13121

---

#### 🔍 Objective:

To systematically review deep learning-based methods for medical image synthesis and their clinical applications, particularly focusing on **inter- and intra-modality transformations**, such as MRI-to-CT, PET-to-CT, and others.

---

#### 🧠 Methodologies Reviewed:

The paper categorizes deep learning approaches into three broad architectures:

- **Autoencoders (AEs)** – used for learning abstract image features.
    
- **U-Net** – popular in medical imaging due to its skip connections for spatial preservation.
    
- **Generative Adversarial Networks (GANs)** – particularly _CycleGAN_ and _conditional GAN_ variants, widely used for unpaired image-to-image translation.
    

It also discusses combinations and adaptations such as:

- Residual networks (ResNet)
    
- Dense blocks
    
- Attention mechanisms
    
- Multi-channel/multi-sequence MRI input
    

---

#### 🧪 Clinical Applications:

1. **MR-to-CT Synthesis**:
    
    - Most studied; crucial for radiation therapy planning and PET attenuation correction.
        
    - Used to reduce radiation exposure and improve soft tissue visualization.
        
    - CycleGAN is highlighted as especially effective for unpaired data.
        
2. **CT/CBCT-to-MR**:
    
    - Supports better soft tissue visualization for segmentation tasks.
        
    - Useful in scenarios like prostate and brain imaging.
        
3. **CBCT-to-CT**:
    
    - For improving image quality in adaptive radiation therapy.
        
    - Deep learning methods outperform conventional correction methods.
        
4. **PET-to-CT and vice versa**:
    
    - Enhances attenuation correction and image quality in functional imaging.
        

---

#### 📊 Metrics for Evaluation:

- Mean Absolute Error (MAE)
    
- Structural Similarity Index (SSIM)
    
- Peak Signal-to-Noise Ratio (PSNR)
    
- Dice Similarity Coefficient (DSC) for segmentation tasks
    
- Dosimetric differences in radiation therapy planning
    
- Bias and variance in PET attenuation correction
    

---

#### 🚧 Challenges Identified:

- Misalignment in paired datasets
    
- Poor contrast between tissues (e.g., bone and air in MRI)
    
- Limited availability of multi-sequence MRI
    
- Generalizability across different scanners and patient populations
    

---

#### 🔬 Future Directions:

- Enhanced CycleGAN variants
    
- Better loss functions (perceptual, mutual information)
    
- Incorporation of multiple MR sequences or modalities
    
- Use of attention and domain-adaptive learning
    

---

### 📚 IEEE Citation:

```copy
T. Wang, Y. Lei, Y. Fu, J. F. Wynne, W. J. Curran, T. Liu, and X. Yang, “A review on medical imaging synthesis using deep learning and its clinical applications,” _J. Appl. Clin. Med. Phys._, vol. 22, no. 1, pp. 11–36, Jan. 2021, doi: 10.1002/acm2.13121.
```
