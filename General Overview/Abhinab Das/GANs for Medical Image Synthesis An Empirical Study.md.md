## Type of Paper

Survey / Empirical Study

## Authors

Youssef Skandarani, Pierre-Marc Jodoin, Alain Lalande

## Citation

Y. Skandarani, P.-M. Jodoin, and A. Lalande, "GANs for Medical Image Synthesis: An Empirical Study," _arXiv preprint_, 2021, doi: [10.48550/arXiv.2105.05318](https://arxiv.org/abs/2105.05318).

## Description

This paper conducts an empirical study of GANs (DCGAN, StyleGAN, etc.) for medical image synthesis, focusing on their effectiveness in generating realistic images for tasks like segmentation and classification across various medical imaging modalities.

## Methodology

The study compares multiple GAN architectures (DCGAN, StyleGAN, etc.) using a standardized evaluation framework. It assesses image quality and utility for downstream tasks using metrics like FID and classification accuracy.

## Training & Dataset

Datasets include CheXpert (chest X-rays), ISIC 2018 (skin lesions), and BraTS 2018 (brain MRI). Training details vary by GAN model, typically using NVIDIA GPUs and Adam optimizer.

## Limitations

Results vary by dataset and model; some GANs struggle with high-resolution medical images due to computational constraints.

## Advantages

Provides a comprehensive benchmark for GAN performance, guiding model selection for medical image synthesis tasks.

## Applications

Image synthesis for data augmentation, segmentation, and classification in medical imaging.

## Evaluation Metrics

Fréchet Inception Distance (FID), Precision, Recall, F1-score for downstream tasks.