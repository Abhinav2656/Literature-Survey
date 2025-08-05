## Type of Paper

Research

## Authors

Qianye Yang, Nannan Li, Zixu Zhao, Xingyu Fan, Eric I-Chao Chang, Yan Xu

## Citation

Q. Yang, N. Li, Z. Zhao, X. Fan, E. I.-C. Chang, and Y. Xu, "MRI Cross-Modality Image-to-Image Translation," _Scientific Reports_, vol. 10, no. 3753, 2020, doi: [10.1038/s41598-020-60520-6](https://doi.org/10.1038/s41598-020-60520-6).

## Description

This paper proposes a cross-modality generation framework using conditional GANs (cGANs) for MR image translation, addressing the complexity of brain structures. It achieves state-of-the-art results in cross-modality registration and segmentation, enhancing medical imaging applications.

## Methodology

The framework employs a cGAN with a U-Net-based generator and a PatchGAN discriminator. It uses adversarial loss combined with L1 loss to ensure realistic image generation and structural fidelity. The model is optimized to translate between MRI modalities (e.g., T1 to T2).

## Training & Dataset

Trained on multiple datasets: BraTs2015 (176/44 subjects for training/validation), Iseg2017, MRBrain13, ADNI, and RIRE. Training was performed using NVIDIA Tesla K80 GPUs with the Adam optimizer (learning rate 0.0002).

## Limitations

Generated images may miss tiny anatomical structures, potentially confusing radiologists. The authors note plans for future improvements to address this issue.

## Advantages

Improves registration and segmentation without requiring additional data collection. The framework is versatile for various MRI modalities, offering significant application potential.

## Applications

Cross-modality registration and segmentation in brain MRI, enhancing diagnostic and treatment planning capabilities.

## Evaluation Metrics

Mean Absolute Error (MAE), Peak Signal-to-Noise Ratio (PSNR), Dice score for segmentation accuracy.