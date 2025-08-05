## Type of Paper
Research

## Authors
Ziyuan Xing, Guang Yang, Qihao Zhang, Guangming Zhu

## Citation
Z. Xing, G. Yang, Q. Zhang, and G. Zhu, "Cross-conditioned Diffusion Model for Medical Image to Image Translation," *J. Imaging Inform. Med.*, vol. 37, no. 5, pp. 2111–2122, 2024, doi: [10.1007/s10278-024-01183-x](https://www.researchgate.net/publication/384057150_Cross-conditioned_Diffusion_Model_for_Medical_Image_to_Image_Translation).

## Description
This paper presents a cross-conditioned diffusion model (CDM) for medical image-to-image translation, focusing on MRI and CT, using MRM, MDN, and C-UNet architectures.

## Methodology
The CDM integrates cross-conditioning with diffusion models, using MRM (Multi-Resolution Module), MDN (Multi-Domain Network), and C-UNet for stable and high-quality image translation.

## Training & Dataset
Trained on paired MRI-CT datasets (e.g., RIRE, TCIA). Training used NVIDIA RTX A6000 GPUs with a denoising schedule.

## Limitations
Diffusion models require longer inference times compared to GANs; high computational cost.

## Advantages
Produces high-fidelity images with better stability than GAN-based methods.

## Applications
Medical image translation for cross-modality diagnostics and treatment planning.

## Evaluation Metrics
Peak Signal-to-Noise Ratio (PSNR), Structural Similarity Index (SSIM).