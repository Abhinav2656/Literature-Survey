# Paper Summary: 

**Title**: Unsupervised Learning for Cross-Domain Medical Image Synthesis Using Deformation Invariant Cycle Consistency Networks  
**Authors**: Chengjia Wang, Gillian Macnaught, Giorgos Papanastasiou, Tom MacGillivray, David Newby  
**Institutions**: BHF Centre for Cardiovascular Science and Edinburgh Imaging Facility QMRI, University of Edinburgh, UK  
**Publication**: _arXiv preprint_ ([arXiv:1808.03944](https://arxiv.org/abs/1808.03944)) 1  
**DOI**: [10.48550/arXiv.1808.03944](https://doi.org/10.48550/arXiv.1808.03944) 1 

---

## Abstract
The paper introduces **Deformation Invariant CycleGAN (DicycleGAN)**, a method for cross-domain medical image synthesis that addresses domain-specific nonlinear deformations inherent in CycleGAN. By integrating deformable convolutional layers and novel cycle-consistency losses, DicycleGAN generates aligned synthetic images while preserving anatomical structure. Evaluated on multi-sequence brain MR (IXI dataset) and multi-modality abdominal CT/MR datasets, DicycleGAN outperforms CycleGAN in scenarios with significant deformations, achieving comparable performance in affine-alignable cases.

---

## Key Contributions
1. **DicycleGAN Architecture**:  
   - Incorporates **deformable convolutional layers** into CycleGAN generators to decouple spatial deformations from anatomical content.  
   - Generates two outputs:  
     - *Deformed output*: Used for adversarial training.  
     - *Undeformed output*: Enforces alignment with source images.  
   - Architecture includes "offset convolution" layers to learn spatial deformations (Fig. 2).  

2. **Loss Functions**:  
   - **Adversarial Loss**: Trains generators to produce realistic images and discriminators to distinguish real/fake data.  
   - **Alignment Loss**: Uses normalized mutual information (NMI) to maximize similarity between source and undeformed outputs.  
     $$ \mathcal{L}_{align}^{A,B} = 2 - \text{NMI}(x^A, G^{A→B}(x^A)) - \text{NMI}(x^B, G^{B→A}(x^B)) $$  
   - **Cycle Consistency Losses**:  
     - Standard cycle loss ($\mathcal{L}_{cyc}$): Ensures $G^{B→A}(G^{A→B}(x^A)) ≈ x^A$.  
     - Deformation-invariant cycle loss ($\mathcal{L}_{dicyc}$): Applies cycle consistency to deformed outputs.  
   - Total loss:  
     $$ \mathcal{L}_{DicycleGAN} = \mathcal{L}_{GAN} + \lambda_{align}\mathcal{L}_{align} + \lambda_{cyc}\mathcal{L}_{cyc} + \lambda_{dicyc}\mathcal{L}_{dicyc} $$  
     (Default weights: $\lambda_{cyc} = \lambda_{dicyc} = 10$, $\lambda_{align} = 0.9$).  

---

## Datasets & Preprocessing
1. **IXI Dataset** (Brain MR):  
   - 66 PD- and T2-weighted volumes (116–130 slices each).  
   - Split: 38 training, 28 testing.  
   - Preprocessing: Skull-stripped, resampled to $1.8 \times 1.8 \times 1.8$ mm³, cropped to $128 \times 128$ slices.  

2. **Private Abdominal Dataset**:  
   - 40 T2*-weighted MR and CT volumes from 20 abdominal aortic aneurysm patients.  
   - Preprocessing: Resampled to $1.56 \times 1.56 \times 5$ mm³, cropped to $192 \times 192$ slices.  

---

## Experimental Setup
- **Training**:  
  - Adam optimizer ($\text{lr}=0.0002$ for 100 epochs, linear decay for next 100).  
  - Early stopping based on $\mathcal{L}_{DicycleGAN}$.  
  - Augmentations: Flips, rotations, shearing, translations.  
- **Evaluation Metrics**:  
  - **MSE**, **PSNR**, **SSIM** (calculated for aligned regions in abdominal data).  

---

## Results
1. **IXI Dataset (Brain MR)**:  
   - **Undeformed T2 Synthesis**: DicycleGAN achieves comparable SSIM (0.871 vs. 0.854) and MSE (0.183 vs. 0.186) to CycleGAN.  
   - **Deformed T2 Synthesis**: DicycleGAN outperforms CycleGAN significantly (SSIM: 0.784 vs. 0.608, PSNR: 22.32 vs. 19.52).  

2. **Abdominal CT/MR Synthesis**:  
   - DicycleGAN shows superior performance (SSIM: 0.712 vs. 0.571, PSNR: 23.71 vs. 18.32).  

---

### **Related Work & Citations**
- **CycleGAN**: Original framework by Zhu et al. ([arXiv:1703.10593](https://arxiv.org/abs/1703.10593)) 1.
- **Deformable CNNs**: Inspired by Dai et al. ([arXiv:1703.06211](https://arxiv.org/abs/1703.06211)) 1.

---

### **Limitations & Future Directions**
- **Challenges**:
    - Requires careful tuning of loss weights (e.g., λ=10 for cycle consistency) 1.
    - Limited to rigidly alignable regions in abdominal data 1.
- **Applications**: Potential use in multi-modal image registration 13.

For implementation details, refer to the [arXiv PDF](https://arxiv.org/pdf/1808.03944) 1.

---
## Discussion
- **Strengths**:  
  - Handles domain-specific deformations (e.g., scanner bed misalignment in Fig. 1).  
  - Preserves anatomical structure via NMI alignment loss.  
- **Limitations**:  
  - Requires careful tuning of loss weights.  
  - Evaluation limited to rigidly alignable regions (e.g., aorta) in abdominal data.  

---

## Citations (IEEE Format)

```copy
C. Wang, G. Macnaught, G. Papanastasiou, T. MacGillivray, and D. Newby, "Unsupervised learning for cross-domain medical image synthesis using deformation invariant cycle consistency networks," _BHF Centre for Cardiovascular Science, University of Edinburgh_, Edinburgh, UK, 2021.
```