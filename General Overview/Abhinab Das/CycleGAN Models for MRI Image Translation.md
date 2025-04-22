### 📄 **Paper Summary**

#### **Title**: CycleGAN Models for MRI Image Translation

#### **Authors**: Cassandra Czobit and Reza Samavi

#### **Published**: arXiv, Jan 2024

#### **Objective**:

To investigate the feasibility of using CycleGAN for translating neuroimages between MRI scans taken at different field strengths (3 Tesla ↔ 1.5 Tesla), aiding dataset augmentation and cross-field analysis.

#### **Methods**:

- **Model Architecture**: CycleGAN with PatchGAN discriminators and ResNet-based generators.
    
- **Loss Functions**: Adversarial, cycle consistency, and reconstruction loss.
    
- **Baseline Comparison**: A DCGAN model was also implemented for comparison.
    
- **Datasets**:
    
    - **3T Data**: From UNC-CH (Kitware platform).
        
    - **1.5T Data**: From OpenNeuro (Philips Intera Scanner).
        
- **Preprocessing**: Slices extracted, resized to 256×256, used for training and testing.
    

#### **Results**:

- **CycleGAN** outperformed DCGAN in terms of visual quality and quantitative metrics.
    
    - **3T → 1.5T**: PSNR = 25.69 dB ± 2.49
        
    - **1.5T → 3T**: PSNR = 27.22 dB ± 0.30
        
- **DCGAN** showed signs of **mode collapse** and poor image quality (PSNR ~6–8 dB).
    
- **Back-cycle consistency** (1.5T → 3T → 1.5T) showed better fidelity than forward.
    

#### **Conclusion**:

CycleGAN is effective for intra-modality MRI translation and can aid in medical data augmentation and analysis. Future work includes enhancing datasets and incorporating classification models to further validate synthetic images.

---

### 📚 **IEEE Citation**

```copy
C. Czobit and R. Samavi, _"CycleGAN Models for MRI Image Translation,"_ arXiv preprint arXiv:2401.00023v2, Jan. 2024. [Online]. Available: [https://arxiv.org/abs/2401.00023](https://arxiv.org/abs/2401.00023)
```
