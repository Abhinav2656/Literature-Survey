## Type of Paper
Research

## Authors
Zhen Zhang, Qingbo Kang, Shoubao Su, Xiping Hu

## Citation
Z. Zhang, Q. Kang, S. Su, and X. Hu, "Spatial-aware Attention Generative Adversarial Network for Semi-supervised Anomaly Detection in Medical Image," *J. Imaging Inform. Med.*, vol. 37, no. 6, pp. 2608–2620, 2024, doi: [10.1007/s10278-024-01215-8](https://www.researchgate.net/publication/384624040_Spatial-Aware_Attention_Generative_Adversarial_Network_for_Semi-supervised_Anomaly_Detection_in_Medical_Image).

## Description
This paper proposes SAGAN, a spatial-aware attention GAN for semi-supervised anomaly detection in medical images, leveraging attention mechanisms to enhance detection accuracy.

## Methodology
SAGAN integrates a spatial attention module with a GAN, using adversarial and reconstruction losses to detect anomalies in a semi-supervised setting.

## Training & Dataset
Trained on BraTS 2019 and ISIC 2018 datasets. Training used NVIDIA RTX 2080 Ti GPUs with Adam optimizer.

## Limitations
Requires some labeled data, limiting fully unsupervised applications; attention mechanism increases complexity.

## Advantages
Improves anomaly detection accuracy by focusing on spatial regions of interest.

## Applications
Semi-supervised anomaly detection in MRI and dermoscopy images.

## Evaluation Metrics
Area Under the Curve (AUC), F1-score, Sensitivity.