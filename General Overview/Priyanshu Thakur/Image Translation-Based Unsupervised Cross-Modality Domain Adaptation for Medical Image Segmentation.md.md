
### 📝 **Paper Summary**

- **Title:**  
    **Image Translation-Based Unsupervised Cross-Modality Domain Adaptation for Medical Image Segmentation**
- **Authors:**  
    **Tao Yang** and **Lisheng Wang**
- **Affiliation:**  
    Department of Automation, Shanghai Jiao Tong University, Shanghai, China  
    Emails: yangtao22@sjtu.edu.cn, lswang@sjtu.edu.cn
- **Publication Venue:**  
    **Presented at:**  
    _CrossMoDA Challenge, associated with MICCAI (Medical Image Computing and Computer Assisted Intervention)_ 2022.
- **DOI:**  
    **No DOI provided** in the paper itself.  
    (It appears to be an **arXiv preprint** or MICCAI workshop submission.)  
    The paper does reference _crossMoDA_ challenge materials hosted at arXiv:  
    Example related link: [arXiv:2201.02831](https://arxiv.org/abs/2201.02831),  
    but for this specific paper, no direct DOI is mentioned.
- **Link to Related Challenge (CrossMoDA):**  
    https://crossmoda.grand-challenge.org/
- **Year:**  
    2022

---

#### **Abstract & Motivation:**

Medical image annotation is costly and time-consuming, which limits the applicability of supervised deep learning methods. Furthermore, differences in imaging modalities (e.g., T1 vs. T2 MRIs) lead to domain shifts that negatively affect model performance. The authors propose an **unsupervised cross-modality domain adaptation (UDA)** method leveraging **CycleGAN-based image translation** and **self-training** to address these challenges.

---

#### **Problem Statement:**

- Domain shift due to different imaging modalities
    
- Lack of annotations in the target domain (e.g., non-contrast MRI)
    
- Need for label-efficient training in segmentation tasks
    

---

#### **Methodology Overview:**

1. **Image Translation Using CycleGAN:**
    
    - Translates labeled images from the source modality (e.g., contrast-enhanced T1 MRI) to the target modality (e.g., high-res T2 MRI).
        
    - Used ResNet-based generators and PatchGAN discriminators.
        
    - Applied losses: adversarial, cycle-consistency, and identity loss (with weights 1:10:5).
        
2. **Self-Training Strategy:**
    
    - Train segmentation model on pseudo-target images (generated via CycleGAN) and real labels.
        
    - Use this model to predict pseudo labels for real target images.
        
    - Retrain model using both pseudo images + real labels and real images + pseudo labels.
        
    - Iterate this process 3 times to refine the model.
        
3. **Preprocessing Details:**
    
    - 3D MRI scans sliced along the z-axis and resized to 256×256 using bicubic interpolation.
        
    - Training done in PyTorch with an RTX 3090 GPU.
        

---

#### **Results:**

Achieved strong results on the **crossMoDA 2022 challenge**, targeting vestibular schwannoma (VS) and cochlea segmentation:

- **Mean Dice Similarity Coefficient (DSC)**: 0.8225
    
- **ASSD (Average Symmetric Surface Distance)**: 1.6712 mm for VS, 0.2317 mm for cochlea
    
- The ResNet-based CycleGAN outperformed U-Net variants.
    
- Self-training iterations significantly improved segmentation performance.
    

---

#### **Key Contributions:**

- Demonstrates **CycleGAN’s effectiveness in unpaired image translation for medical imaging**.
    
- Introduces a **simple yet powerful self-training pipeline** for adapting to unlabelled target modalities.
    
- Shows that **public deep learning architectures can achieve strong performance** with no architectural changes, only better domain adaptation techniques.
    

---

### 🔍 **Relation to our Project**

| Aspect      | Paper                          | Your Project                     |
| ----------- | ------------------------------ | -------------------------------- |
| Modalities  | ceT1 MRI → hrT2 MRI            | MRI ↔ CT                         |
| Method      | CycleGAN + Self-Training       | CycleGAN with structural losses  |
| Supervision | Unsupervised domain adaptation | Unpaired image translation       |
| Goal        | Improve segmentation           | High-fidelity modality synthesis |
| Tools       | PyTorch, nnU-Net               | PyTorch, MONAI (likely)          |

The methodology (CycleGAN, identity loss, PatchGAN discriminators, and image-level translation) can be **directly adapted** to our task of MRI-to-CT synthesis. We might not need the self-training step if segmentation is not our goal, but the translation pipeline is very much aligned.

---

### 📚 **IEEE Citation**

```copy
T. Yang and L. Wang, "Image Translation-Based Unsupervised Cross-Modality Domain Adaptation for Medical Image Segmentation," presented at the CrossMoDA Challenge at MICCAI 2022, Shanghai Jiao Tong University, 2022.
```
