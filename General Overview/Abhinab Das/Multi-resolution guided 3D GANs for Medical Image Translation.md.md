## Type of Paper

Research

## Authors

Jiwon Ha, Seongmin Lee, Joonseok Lee

## Citation

J. Ha, S. Lee, and J. Lee, "Multi-resolution guided 3D GANs for Medical Image Translation," _arXiv preprint_, 2025, doi: [10.48550/arXiv.2412.00575](https://arxiv.org/abs/2412.00575).

## Description

This paper proposes a 3D-mDAUNet, a multi-resolution guided 3D GAN for medical image translation, focusing on 3D MRI and CT image synthesis and segmentation tasks.

## Methodology

The 3D-mDAUNet integrates multi-resolution feature extraction with a 3D U-Net-based GAN. It uses adversarial and cycle-consistency losses to ensure accurate 3D image translation.

## Training & Dataset

Trained on 3D MRI and CT datasets (e.g., BraTS, internal datasets). Training utilized NVIDIA V100 GPUs with a multi-resolution pyramid approach.

## Limitations

High computational requirements limit scalability; performance depends on dataset quality.

## Advantages

Handles complex 3D structures effectively, improving translation and segmentation accuracy.

## Applications

3D image translation and segmentation for MRI and CT, aiding in surgical planning.

## Evaluation Metrics

Dice Similarity Coefficient (DSC), Structural Similarity Index (SSIM).