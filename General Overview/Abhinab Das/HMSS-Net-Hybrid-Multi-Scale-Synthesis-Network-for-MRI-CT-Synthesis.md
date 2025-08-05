## Type of Paper
Research

## Authors
Yuxiang Li, Wenlong Guo, Yue Zhao, Jingjing Xiao, Yongchao Liu, Shuxue Ding

## Citation
Y. Li, W. Guo, Y. Zhao, J. Xiao, Y. Liu, and S. Ding, "HMSS-Net: Hybrid Multi-Scale Synthesis Network for MRI-CT Synthesis," *Frontiers in Physics*, vol. 11, 2023, doi: [10.3389/fphy.2023.1088899](https://doi.org/10.3389/fphy.2023.1088899).

## Description
This paper introduces HMSS-Net, a hybrid Transformer-CNN model for MRI-to-CT synthesis, leveraging multi-scale features for improved synthesis quality in medical imaging.

## Methodology
HMSS-Net combines a Transformer for global feature extraction with a CNN for local details. It uses a multi-scale feature fusion strategy and adversarial loss to generate realistic CT images from MRI.

## Training & Dataset
Trained on paired MRI-CT datasets (e.g., RIRE, internal hospital data). Training used NVIDIA RTX 3090 GPUs with Adam optimizer.

## Limitations
Requires paired data for training, limiting applicability in unpaired scenarios.

## Advantages
Superior synthesis quality due to hybrid architecture, enhancing diagnostic accuracy.

## Applications
MRI-to-CT synthesis for radiotherapy planning and cross-modality diagnosis.

## Evaluation Metrics
Mean Absolute Error (MAE), Peak Signal-to-Noise Ratio (PSNR).