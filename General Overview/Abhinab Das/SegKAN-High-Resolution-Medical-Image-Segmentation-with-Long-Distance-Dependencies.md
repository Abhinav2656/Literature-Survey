## Type of Paper
Research

## Authors
Shanzhen Tan, Hao Wang, Jianjun Zhang

## Citation
S. Tan, H. Wang, and J. Zhang, "SegKAN: High-Resolution Medical Image Segmentation with Long-Distance Dependencies," *arXiv preprint*, 2024, doi: [10.48550/arXiv.2412.19990](https://arxiv.org/html/2412.19990v1).

## Description
This paper introduces SegKAN, a model for high-resolution medical image segmentation, using FKAC and PTSN modules to capture long-distance dependencies.

## Methodology
SegKAN combines Fast Kernel Attention Convolution (FKAC) and Pyramid Transformer Spatial Network (PTSN) with a GAN-based framework for precise segmentation.

## Training & Dataset
Trained on BraTS 2020 and ISIC 2019 datasets. Training used NVIDIA A100 GPUs with a batch size of 16.

## Limitations
High computational cost due to transformer-based architecture; requires large datasets.

## Advantages
Captures long-distance dependencies, improving segmentation accuracy for complex structures.

## Applications
High-resolution segmentation in MRI and dermoscopy images.

## Evaluation Metrics
Dice Similarity Coefficient (DSC), Intersection over Union (IoU).