
## 🧠 Summary

- **Title**:  
    **MedPrompt: Cross-Modal Prompting for Multi-Task Medical Image Translation**
- **Authors**:
    - Xuhang Chen (Shenzhen Institutes of Advanced Technology, Chinese Academy of Sciences)
    - Chi-Man Pun (University of Macau)
    - Shuqiang Wang (Shenzhen Institutes of Advanced Technology, Chinese Academy of Sciences)
- **Publication Source**:
    - **Preprint** at **arXiv**
    - **arXiv ID**: **2310.02663**
- **DOI**:
    - **DOI is currently not assigned** (since it's an arXiv preprint), but the official arXiv link is: [https://arxiv.org/abs/2310.02663](https://arxiv.org/abs/2310.02663)
- **Date of Submission**:
    - **4th October 2023**
- **Published Format**:
    - arXiv Preprint under **Computer Vision and Pattern Recognition (cs.CV)** category

### **Problem Addressed**

Current deep learning models for medical image translation struggle with:

- Modality-specific adaptability
    
- Capturing global context
    
- Generalizing across multiple modality pairs (e.g., MRI↔CT, MRI↔PET)
    

### **Proposed Solution**

**MedPrompt**, a **Transformer-based multi-task image translation model** enhanced with **visual prompting**. It introduces:

- A **Self-adaptive Prompt Block (SPB)** containing:
    
    - **Prompt Extraction Block (PEB)** – extracts modality-aware prompts dynamically based on the input
        
    - **Prompt Fusion Block (PFB)** – merges prompts with feature maps using a Transformer
        
- A **Transformer encoder-decoder** backbone, providing global context and scalability
    

This framework enables **efficient, generalizable, and structurally consistent** image translation across multiple medical domains.

---

### **Methodology Overview**

- **Input**: Multi-modal medical images (e.g., MRI, CT, PET)
    
- **Backbone**: Modified Transformer blocks (MDTA + GDFN layers from Restormer)
    
- **Prompt Blocks**:
    
    - PEB uses learnable embeddings and global average pooling to condition prompts
        
    - PFB fuses input features with prompts via concatenation and transformer encoding
        
- **Loss Functions**:
    
    - **MSE + SSIM**, with a weighted combination to balance pixel-wise and perceptual similarity
        

---

### **Datasets Used**

1. **IXI**: MRI (T1 ↔ T2)
    
2. **BraTS2020**: MRI (T1 ↔ T2)
    
3. **ADNI**: MRI ↔ PET
    
4. **SynthRAD2023**: MRI ↔ CT, CBCT ↔ CT
    

---

### **Evaluation Metrics**

- **PSNR**, **SSIM**, and **MAE**
    
- Compared against 13 methods including CycleGAN, pGAN, medSynth, ResViT
    

---

### **Results**

- Outperforms **CycleGAN, pGAN, ResViT, U-Net**, etc., in **PSNR, SSIM, and MAE** on all datasets
    
- Demonstrates strong generalization across domains
    
- Ablation studies confirm the effectiveness of **PEB**, **PFB**, and **Transformer blocks**
    

---

### **Key Insights for our Project**

- **Prompting + Transformers** > pure CNNs in cross-modal translation
    
- Learnable prompt conditioning improves **modality adaptability**
    
- Can serve as a **next-gen extension to CycleGAN**
    
- Shows value of **multi-task training** and **global context** in medical imaging
    

---

## 📘 IEEE Citation (formatted)

```copy
X. Chen, C.-M. Pun and S. Wang, "MedPrompt: Cross-Modal Prompting for Multi-Task Medical Image Translation," _arXiv preprint arXiv:2310.02663_, Oct. 2023. [Online]. Available: [https://arxiv.org/abs/2310.02663](https://arxiv.org/abs/2310.02663)
```
