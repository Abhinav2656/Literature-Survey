## Type of Paper
Research

## Authors
Hao Chen, Tianxiang Chen, Shujun Wang, Chen Zhang

## Citation
H. Chen, T. Chen, S. Wang, and C. Zhang, "Adapting Large Pre-trained Generative Models for Medical Image Data Augmentation," in *Proc. Int. Conf. Med. Image Comput. Comput.-Assist. Interv. (MICCAI)*, 2024, pp. 1–10, doi: [10.1007/978-3-031-72086-4_27](https://papers.miccai.org/miccai-2024/paper/2585_paper.pdf).

## Description
This paper proposes MAGE, a Masked Generative Encoder, for few-shot medical image data augmentation using pre-trained generative models.

## Methodology
MAGE adapts a pre-trained GAN with a masked encoder, using adversarial and reconstruction losses to generate diverse medical images in a few-shot setting.

## Training & Dataset
Trained on limited medical imaging datasets (e.g., CheXpert, ISIC). Fine-tuning used NVIDIA RTX A6000 GPUs.

## Limitations
Performance depends on pre-trained model quality; limited by few-shot data availability.

## Advantages
Effective in low-data scenarios, leveraging pre-trained models for high-quality augmentation.

## Applications
Few-shot data augmentation for medical imaging tasks like classification and segmentation.

## Evaluation Metrics
Fréchet Inception Distance (FID), classification accuracy.