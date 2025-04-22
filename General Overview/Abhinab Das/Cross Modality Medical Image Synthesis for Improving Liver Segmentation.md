## 📘 Paper Summary

### **Title**:

_Cross Modality Medical Image Synthesis for Improving Liver Segmentation_

### **Authors**:

Muhammad Rafiq, Hazrat Ali, Ghulam Mujtaba, Zubair Shah, Shoaib Azmat

### **Objective**:

To generate synthetic abdominal MRI images from unpaired CT scans using a CycleGAN-based architecture (EssNet), and to use these synthesized images to improve the performance of a U-Net-based liver segmentation model.

---

### **Key Contributions**:

1. **EssNet+U-Net Pipeline**:
    
    - **Stage 1**: Uses **EssNet**, a CycleGAN-inspired network, to synthesize high-quality MRI images from CT scans, tackling domain deformation and alignment issues.
        
    - **Stage 2**: Trains a **U-Net segmentation model** on both real and synthetic MRI images, showing improved liver segmentation.
        
2. **Unpaired Translation**:  
    Utilizes the CHAOS dataset with unpaired CT and MRI data, making the technique practical and adaptable to real-world scenarios where paired data is scarce.
    
3. **Loss Design**:
    
    - Adversarial Loss
        
    - Cycle Consistency Loss
        
    - Segmentation Loss (via auxiliary segmentation branch in EssNet)
        
4. **Ablation Study**: Demonstrates that removing the segmentation component in EssNet (i.e., plain CycleGAN) leads to **alignment issues** and **no improvement** in segmentation, justifying the need for domain-adaptive design.
    

---

### **Results**:

- **Dice Coefficient** improved from 0.9459 to **0.9524**
    
- **IoU** improved from 0.8974 to **0.9091**
    
- Segmentation on synthetic + real data outperformed models trained on real data only.
    
- **Training Times**: ~6.5 hours per model on RTX 2060; inference up to 21 FPS
    
- **Limitations**: Evaluation limited to a single institution's dataset and only U-Net as the segmentation baseline.
    

---

### **Implications for Your Project**:

- Reinforces the use of **CycleGAN-based models** for **MRI–CT translation**.
    
- Validates that **unpaired training** can still yield clinically useful outputs.
    
- Highlights the importance of addressing **alignment** and **domain deformation**—you could adapt EssNet or similar mechanisms in your implementation.
    
- Suggests a practical downstream evaluation method (segmentation accuracy) to measure anatomical fidelity in synthesized outputs.

### 📎 IEEE Citation Format

```copy
M. Rafiq, H. Ali, G. Mujtaba, Z. Shah and S. Azmat, "Cross Modality Medical Image Synthesis for Improving Liver Segmentation," *arXiv preprint arXiv:2503.00945*, Mar. 2025. [Online]. Available: https://arxiv.org/abs/2503.00945
```

