## 🧠 **Overview of the Paper**

**Authors**: Muhammad Rafiq, Hazrat Ali, Ghulam Mujtaba, Zubair Shah, Shoaib Azmat   
**Published**: arXiv, Mar 2025    
**DOI:** [10.48550/arXiv.2503.00945](https://doi.org/10.48550/arXiv.2503.00945).   

---

### 🎯 **Problem Statement**

Deep learning for medical imaging (e.g., segmentation, diagnosis) typically requires large labeled datasets. However, acquiring such datasets—especially for MRI and CT scans is:

- **Expensive** and **time-consuming**
    
- Dependent on **radiologist annotations**
    
- Constrained by **privacy and access issues**
    

To address this, the authors explore **cross-modality image synthesis**: translating **abdominal CT scans into MRI images** using **unpaired data**. The core goal is to **augment the MRI dataset** with synthetic images and **improve liver segmentation accuracy** using U-Net.

<img src="Assets/two-stage (EssNet+U-Net) approach.png" alt="" width="600"/>


---

## 🏗️ **Architecture and Methodology**

The authors propose a **two-stage deep learning pipeline**:

<img src="Assets/workflow of the EssNet architecture.png" alt="" width="600"/>

### 🔧 **1. EssNet (Enhanced CycleGAN for Image Synthesis)**

- **EssNet** is an improved **CycleGAN** model with a key addition: a **segmentation branch** integrated into the generator architecture.
    
- This design not only translates CT → MRI, but also **simultaneously performs segmentation** of the synthesized images, thereby improving anatomical alignment.
    

**EssNet Components:**

- **CycleGAN Core**: 2 Generators (CT → MRI, MRI → CT), 2 Discriminators (PatchGAN style)
    
- **Segmentation Network**: A **9-block ResNet** acting on synthesized MRI images to help guide the generator toward producing anatomically accurate images.
    
- **Loss Functions**:
    
    - **Adversarial Loss**: Ensures synthetic images are indistinguishable from real ones.
        
    - **Cycle Consistency Loss**: Enforces bidirectional mapping—CT→MRI→CT ≈ CT.
        
    - **Segmentation Loss**: Helps the generator produce deformation-free, aligned images by penalizing inaccurate segmentation predictions on synthetic MRI.
        
- **Training Strategy**: Trained on **unpaired** abdominal CT and MRI data from the CHAOS dataset.

### 🔍 **2. U-Net for Liver Segmentation**

- The U-Net is trained in two settings:
    
    - Using **only real MRI images**
        
    - Using **real + synthetic MRI images** (from EssNet)
        
- The improvement in segmentation is evaluated using:
    
    - **Dice Coefficient**
        
    - **Intersection over Union (IoU)**
        

---

## 📊 **Results and Key Findings**

| Metric | Real Only (350 MRI) | Real + Synthetic (1064 MRI) | Improvement |
| ------ | ------------------- | --------------------------- | ----------- |
| Dice   | 0.9459              | **0.9524**                  | +0.65%      |
| IoU    | 0.8974              | **0.9091**                  | +1.17%      |

- **Ablation Study**: Replacing EssNet with plain CycleGAN (no segmentation branch) results in:
    
    - **Geometric distortions**
        
    - Poorer alignment
        
    - **No significant improvement** in segmentation performance
        
- **Computational Efficiency**:
    
    - Trained on an RTX 2060 (6GB) GPU
        
    - EssNet and U-Net models have ~28M and ~31M parameters, respectively
        
    - Inference speeds: U-Net reaches **21 FPS**, usable in real-time scenarios
        

---

## 🧩 **Key Contributions**

1. **Two-stage architecture** (EssNet + U-Net) to use unpaired CT to synthesize MRI images and improve downstream segmentation.
    
2. **Segmentation-guided synthesis** to address deformation and misalignment problems common in unpaired GAN-based image translation.
    
3. **Demonstrated empirical gains** in segmentation metrics by augmenting training data with cross-modality synthetic images.
    
4. **Ablation analysis** proving the superiority of EssNet over vanilla CycleGAN in preserving anatomical structure.
    

---

## 🔬 **Research Gaps Addressed**

| Existing Challenge                                 | Solution in This Paper                                         |
| -------------------------------------------------- | -------------------------------------------------------------- |
| Lack of paired data for cross-modality translation | Use of CycleGAN-style architecture (EssNet) with unpaired data |
| Misalignment in synthetic images                   | Segmentation-aware generation network                          |
| Small labeled datasets for MRI                     | Synthetic MRI generation from CT scans to expand dataset       |
| Poor generalization of deep models on small data   | Data augmentation via domain translation                       |

---

## ⚠️ **Limitations and Scope for Improvement**

1. **Dataset Generalization**: Experiments are limited to the CHAOS dataset from a single hospital. Results may not generalize to other domains or scanners.
    
2. **Segmentation Model Choice**: Only U-Net was used. Advanced models (like nnUNet, TransUNet) could further validate general applicability.
    
3. **Quality of Synthetic Data**: Some minor defects still occur in synthesized MRI images (e.g., missing liver edge portions). Future work could explore better generator architectures or 3D modeling.
    
4. **Evaluation by Experts**: No clinical/radiologist validation of synthesized images is provided.
    

---

## 🔄 **Relation to our Project**

This paper is highly applicable to our project, which targets **MRI ⇌ CT unpaired translation** for general medical use:

- Reinforces the use of **CycleGAN-like frameworks** for **unpaired image-to-image translation**
    
- Addresses one of your listed challenges: **preserving anatomical correctness**
    
- Provides a practical validation pathway: use **segmentation performance** as a proxy to evaluate clinical utility
    
- Suggests an upgrade path: **EssNet-style segmentation-aware training** could be integrated into your system

---

### 📎 IEEE Citation Format

```copy
M. Rafiq, H. Ali, G. Mujtaba, Z. Shah and S. Azmat, "Cross Modality Medical Image Synthesis for Improving Liver Segmentation," *arXiv preprint arXiv:2503.00945*, Mar. 2025. [Online]. Available: https://arxiv.org/abs/2503.00945
```
