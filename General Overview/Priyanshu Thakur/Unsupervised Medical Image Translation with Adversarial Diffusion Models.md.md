
## 📄 **Overview of the Paper**

**Authors**: Muzaffer Özbey, Onat Dalmaz, Salman UH Dar, Hasan A Bedel, Şaban Öztürk, Alper Güngör, Tolga Çukur  
**Affiliations:**
- Department of Electrical and Electronics Engineering, and the National Magnetic Resonance Research Center (UMRAM), Bilkent University, Ankara, Turkey   
- Amasya University, Turkey (Ş. Öztürk)   
- ASELSAN Research Center, Turkey (A. Güngör)   
**Published on**: March 31, 2023 (arXiv version 3)   
**DOI:** Not published yet in a journal (still a preprint). [arXiv:2207.08208](https://arxiv.org/abs/2207.08208)    

---
## Introduction

Medical imaging often requires multiple modalities (e.g., MRI and CT) to provide complementary diagnostic information. However, acquiring multiple modalities is costly and time-consuming. Thus, there is a growing need for **cross-modality image translation** — synthesizing one modality from another to eliminate the need for redundant scans.

Traditional solutions have used **Generative Adversarial Networks (GANs)**, but they suffer from problems like mode collapse, poor diversity, and lack of explicit likelihood modeling. On the other hand, **diffusion models**—which gradually refine random noise into an image—offer better fidelity and stability but are computationally intensive and difficult to adapt for unpaired data (common in medical datasets).

To address these gaps, the paper proposes a novel method called **SynDiff**:  
an **adversarial diffusion model** for **unsupervised medical image translation** that efficiently synthesizes target modality images from a source modality.

---

## Motivation

- **GAN-based models**: Excellent realism but unstable training, implicit distribution modeling, poor diversity.
    
- **Diffusion models**: Better fidelity, explicit modeling of likelihood, but high computational load and difficulty handling unpaired datasets.
    
- **Need**: A model that combines the strengths of GANs and diffusion models, while being computationally efficient and working with unpaired datasets.
    

---

## Main Contributions

1. **SynDiff** is introduced as the **first adversarial diffusion model** for **high-fidelity** medical image synthesis.
    
2. It enables **unsupervised learning** using a **cycle-consistent architecture**.
    
3. It proposes a **source-conditional adversarial projector** to perform efficient sampling over large diffusion steps — drastically reducing inference time compared to conventional diffusion models.
    
4. It supports translation between different **MRI contrasts** (T1, T2, PD) and between **MRI-CT modalities**.
    
5. The model's code is made publicly available for reproducibility.
    

---

## Technical Approach

| Aspect            | Details                                                                                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Task**          | Cross-modality medical image translation (e.g., MRI ↔ CT)                                                                                                          |
| **Learning Type** | **Unsupervised** (unpaired data)                                                                                                                                   |
| **Main Model**    | **SynDiff** (Adversarial Diffusion Model)                                                                                                                          |
| **Base**          | Modified Denoising Diffusion Probabilistic Models (DDPM)                                                                                                           |
| **Conditioning**  | Guides diffusion with source modality images                                                                                                                       |
| **Acceleration**  | Large step sizes (T/k steps) for fast sampling                                                                                                                     |
| **Architecture**  | Cycle-consistent architecture with both diffusive and non-diffusive modules                                                                                        |
| **Novelty**       | - Adversarial projector for large-step reverse diffusion  <br>- Conditional diffusion guided by source modality  <br>- Cycle-consistency for unsupervised learning |
| **Libraries**     | PyTorch, custom MONAI tools                                                                                                                                        |

### 1. **Adversarial Diffusion Process**

- Instead of the traditional small-step diffusion (requiring thousands of steps), SynDiff uses **large diffusion steps (T/k steps)** for efficiency.
    
- The **adversarial projector** helps denoise the noisy intermediate images accurately even with large step sizes.
    
- The generator predicts an intermediate clean image, and a discriminator distinguishes real versus generated denoised images.
    

### 2. **Cycle-Consistent Architecture**

- Since paired datasets are rare, SynDiff uses **bilateral translation** between modalities.
    
- **Non-diffusive modules** estimate corresponding source images for unpaired training images.
    
- **Diffusive modules** then synthesize the target images guided by these estimates.
    
- A **cycle-consistency loss** ensures that translations preserve anatomical information.
    

### 3. **Loss Functions**

- **Adversarial Loss**: For the generator and discriminator interplay.
    
- **Cycle Consistency Loss**: Enforces that a source image can be reconstructed from a generated target image.
    
- **Pixel-wise Losses**: Help fine-tune image details.
    

### 4. **Network Architectures**

- **Generator**: U-Net-like architecture with skip connections.
    
- **Discriminator**: PatchGAN discriminator, efficient and robust to high-frequency artifacts.
    

---

## Experiments

### Datasets

- **IXI Dataset** (brain MRI): T1, T2, PD contrasts.
    
- **BRATS Dataset** (brain tumors MRI): T1, T2, FLAIR contrasts.
    
- **Pelvic Dataset**: MRI and CT scans.
    

All datasets underwent preprocessing steps like normalization, registration, and resampling to a fixed size (256x256).

### Competing Methods

- Traditional GAN-based models: cGAN, UNIT, MUNIT, AttGAN, SAGAN.
    
- Recent diffusion models: DDPM, UNIT-DDPM.
    

### Metrics

- **Peak Signal-to-Noise Ratio (PSNR)**: Image quality.
    
- **Structural Similarity Index (SSIM)**: Preservation of structural features.
    
- **Fréchet Inception Distance (FID)**: Distribution similarity for unconditional synthesis.
    

---

## Results

### 1. **Multi-Contrast MRI Translation**

- SynDiff consistently **outperformed** all baseline methods across multiple tasks (T1↔T2, T1↔PD, T2↔PD).
    
- Achieved higher PSNR and SSIM scores.
    
- Synthesized images had **lower noise, fewer artifacts**, and **better structural fidelity** compared to GANs and conventional diffusion models.
    

### 2. **Multi-Modal MRI-CT Translation**

- SynDiff showed strong performance even in **MRI→CT translation**, a much harder task due to modality differences.
    
- Maintained better anatomical structure in synthetic CT images compared to baselines.
    

### 3. **Computational Efficiency**

- SynDiff’s fast diffusion sampling reduced inference times by **over 400x** compared to conventional diffusion models.
    
- Memory consumption was reasonable (lower than classic diffusion models, comparable to GANs).
    

---
## Ablation Studies

Several variant models were tested:

- **Without adversarial loss**: Performance dropped drastically.
    
- **Without cycle consistency**: Structural details were poorly preserved.
    
- **Without the diffusive module**: Quality and realism deteriorated.
    
- Also studied the impact of varying diffusion steps (T/k) and weights for loss terms — SynDiff remained robust across configurations.
    

---

## Key Strengths

✅ High-fidelity synthetic images  
✅ Works with unpaired datasets (unsupervised learning)  
✅ Efficient sampling (very fast inference)  
✅ Consistent superiority over both GANs and vanilla diffusion models  
✅ Open-source code

---

## Limitations

- SynDiff requires **significant GPU resources** during training (although inference is much faster).
    
- Currently tested only on 2D slices — extending to **3D volumes** could be an important future direction.
    

---

## Conclusion

**SynDiff** provides a **powerful, efficient, and unsupervised solution** for **medical image translation** across modalities. By marrying adversarial learning with diffusion modeling, it overcomes the limitations of existing approaches. It opens up possibilities for reduced radiation exposure, cost-saving in imaging protocols, and broader multi-modal imaging accessibility in clinical practice.

---

# 📚 Citation (IEEE Format)

Here’s the proper citation in IEEE style:

```copy
M. Özbey, O. Dalmaz, S. U. H. Dar, H. A. Bedel, Ş. Öztürk, A. Güngör, and T. Çukur, “Unsupervised Medical Image Translation with Adversarial Diffusion Models,” _arXiv preprint arXiv:2207.08208_, Mar. 2023. [Online]. Available: [https://arxiv.org/abs/2207.08208](https://arxiv.org/abs/2207.08208)
```