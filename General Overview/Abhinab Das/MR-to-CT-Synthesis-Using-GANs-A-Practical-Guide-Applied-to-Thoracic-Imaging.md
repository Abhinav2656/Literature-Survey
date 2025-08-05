## Type of Paper
Research

## Authors
Antoine Le Guen, Pierre-Yves Brulin, Julien Le Marec, Julien Lejeune

## Citation
A. Le Guen, P.-Y. Brulin, J. Le Marec, and J. Lejeune, "MR to CT Synthesis Using GANs: A Practical Guide Applied to Thoracic Imaging," in *Proc. 12th Int. Conf. Image Process. Theory, Tools Appl. (IPTA)*, 2023, pp. 1–6, doi: [10.5220/0011895700003411](https://www.scitepress.org/Papers/2023/118957/118957.pdf).

## Description
This paper provides a practical guide for MR-to-CT lung synthesis using GANs (CycleGAN, pix2pixHD, SPADE, NICE-GAN), focusing on thoracic imaging applications.

## Methodology
Compares multiple GANs: CycleGAN (cycle-consistency loss), pix2pixHD (paired data), SPADE (spatially-adaptive normalization), and NICE-GAN (improved stability). Each model is optimized for lung CT synthesis from MRI.

## Training & Dataset
Trained on paired and unpaired MRI-CT datasets (e.g., internal thoracic datasets). Training used NVIDIA A100 GPUs with varying batch sizes.

## Limitations
Performance varies by GAN; unpaired models may produce less accurate results.

## Advantages
Provides a practical framework for selecting GANs based on data availability and application needs.

## Applications
MR-to-CT synthesis for lung imaging in radiotherapy and diagnostics.

## Evaluation Metrics
Fréchet Inception Distance (FID), Structural Similarity Index (SSIM).