### 📘 **Comprehensive Summary**

#### 📌 **Title**: HLSNC-GAN: Medical Image Synthesis Using Hinge Loss and Switchable Normalization in CycleGAN

#### 📅 Published: April 2024, IEEE Access

#### 👨‍💻 Authors: Yang Heng, Ma Yinghua, Fiaz Gul Khan, Ahmad Khan, and Zeng Hui

#### 🔍 **Objective**

To improve unpaired MRI-to-CT and CT-to-MRI synthesis using a modified CycleGAN framework that addresses structural consistency, image diversity, and training instability.

---

#### 🧠 **Key Contributions**

1. **Hinge Loss Function**: Introduced in the generator and discriminator to enhance adversarial learning, reduce blurriness, and ensure better structural fidelity than standard GAN losses.
    
2. **Switchable Normalization (SN)**: Replaces fixed normalization methods like BatchNorm/InstanceNorm with dynamic selection to improve training stability and adaptiveness across datasets.
    
3. **RMSProp Optimizer**: Offers adaptive learning rates and reduces training instability, outperforming common optimizers like Adam and SGD.
    
4. **Improved Architecture**:
    
    - Generators use ResNet blocks with skip connections for detail preservation.
        
    - Discriminators employ SN and LeakyReLU for better convergence and classification accuracy.
        
5. **Loss Functions**:
    
    - Adversarial loss
        
    - Cycle-consistency loss
        
    - Identity loss
        
    - Hinge loss
        
    - Combined into a total loss weighted by λ.
        

---

#### 🧪 **Experimental Setup**

- **Datasets**: Both _unpaired (Kaggle)_ and _paired (A40B57)_ datasets for MRI-CT.
    
- **Resolution**: Images resized to 512×512 or 512×256.
    
- **Hardware**: NVIDIA RTX 3080 GPU.
    
- **Training**: 500 epochs with batch size 1.
    
- **Evaluation Metrics**: PSNR, SSIM.
    

---

#### 📊 **Results**

- Outperformed traditional CycleGAN and other state-of-the-art models in both PSNR and SSIM.
    
- Achieved:
    
    - **MRI→CT**: PSNR = 52.484, SSIM = 0.969
        
    - **CT→MRI**: PSNR = 51.051, SSIM = 0.949
        
- Demonstrated strong performance on both paired and unpaired data.
    

---

#### ⚠️ **Limitations**

- Higher computational requirements due to added complexity.
    
- Generalization to other modalities (e.g., PET, SPECT) remains untested.
    
- Scalability and robustness across larger and more diverse datasets need further exploration.
    

---

#### 🔮 **Future Work**

- Extend model to 3D/4D modalities.
    
- Integrate PET/SPECT.
    
- Validate synthetic images in clinical settings.
    
- Explore other loss/normalization techniques and multi-modal fusion.
    

---

### 📚 **IEEE Citation**

```copy
Y. Heng, M. Yinghua, F. G. Khan, A. Khan, and Z. Hui, "HLSNC-GAN: Medical Image Synthesis Using Hinge Loss and Switchable Normalization in CycleGAN," _IEEE Access_, vol. 12, pp. 55448–55463, Apr. 2024, doi: 10.1109/ACCESS.2024.3390245.
```
