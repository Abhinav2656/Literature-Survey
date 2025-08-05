## Type of Paper

Research

## Authors

Cory M. Johnson, Neil A. Tenenholtz, Katherine P. Andriole

## Citation

C. M. Johnson, N. A. Tenenholtz, and K. P. Andriole, "Synthetic Medical Imaging Generation with Generative Adversarial Networks for Plain Radiographs," _Applied Sciences_, vol. 14, no. 15, p. 6831, 2024, doi: [10.3390/app14156831](https://doi.org/10.3390/app14156831).

## Description

This paper presents a GAN-based pipeline (GIST) using StyleGAN3 for high-resolution radiograph synthesis, addressing data scarcity and privacy issues in medical imaging through data augmentation.

## Methodology

The GIST pipeline uses StyleGAN3 with adaptive discriminator augmentation. It employs a progressive growing strategy and style mixing to generate high-quality synthetic radiographs.

## Training & Dataset

Trained on a dataset of knee and elbow X-rays (specific dataset not named, assumed internal). Training used NVIDIA A100 GPUs with a batch size of 32.

## Limitations

Synthetic images may not fully capture rare pathologies, and clinical validation is needed to ensure diagnostic reliability.

## Advantages

Reduces reliance on patient data, enhancing privacy and enabling data augmentation for rare conditions.

## Applications

Data augmentation for radiograph-based diagnosis, particularly for low-incidence pathologies.

## Evaluation Metrics

Fréchet Inception Distance (FID), clinical evaluation by radiologists.