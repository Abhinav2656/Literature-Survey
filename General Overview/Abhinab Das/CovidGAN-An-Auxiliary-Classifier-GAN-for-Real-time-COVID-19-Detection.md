## Type of Paper
Research

## Authors
Abdul Waheed, Muskan Goyal, Nitin Mittal, Shubham Shankar, Musheer Ahmad, Alok Negi

## Citation
A. Waheed, M. Goyal, N. Mittal, S. Shankar, M. Ahmad, and A. Negi, "CovidGAN: An Auxiliary Classifier GAN for Real-time COVID-19 Detection," *J. Med. Syst.*, vol. 45, no. 5, p. 54, 2021, doi: [10.1007/s10916-021-01724-x](https://doi.org/10.1007/s10916-021-01724-x).

## Description
This paper presents CovidGAN, an Auxiliary Classifier GAN (ACGAN) for generating synthetic chest X-rays to improve real-time COVID-19 detection.

## Methodology
CovidGAN uses an ACGAN with an auxiliary classifier to generate labeled synthetic X-rays. It combines adversarial and classification losses for realistic image generation.

## Training & Dataset
Trained on a dataset of chest X-rays (e.g., COVIDx dataset). Training used NVIDIA GTX 1080 Ti GPUs with Adam optimizer.

## Limitations
Synthetic images may not capture all COVID-19 variations; requires clinical validation.

## Advantages
Enhances COVID-19 detection by augmenting limited datasets, improving classifier performance.

## Applications
Data augmentation and classification for COVID-19 detection in chest X-rays.

## Evaluation Metrics
Accuracy, Sensitivity, Specificity, F1-score.