## Type of Paper

Research

## Authors

Changhee Han, Leonardo Rundo, Kohei Murao, Evis Sala, Hideki Nakayama, Shin’ichi Satoh

## Citation

C. Han, L. Rundo, K. Murao, E. Sala, H. Nakayama, and S. Satoh, "MADGAN: unsupervised medical anomaly detection GAN using multiple adjacent brain MRI slice reconstruction," _BMC Bioinformatics_, vol. 22, no. 2, p. 31, 2021, doi: [10.1186/s12859-020-03936-1](https://doi.org/10.1186/s12859-020-03936-1).

## Description

This paper introduces MADGAN, a GAN-based model for unsupervised anomaly detection in brain MRI by reconstructing multiple adjacent slices, leveraging Wasserstein GAN with Gradient Penalty (WGAN-GP) for improved stability and detection performance.

## Methodology

MADGAN uses a WGAN-GP framework with multiple generators reconstructing adjacent MRI slices. It employs Wasserstein loss with gradient penalty to stabilize training and detect anomalies by comparing reconstructed and original slices.

## Training & Dataset

Trained on the BraTS 2018 dataset (285 subjects) and HCP dataset, using T1-weighted and T2-weighted MRI scans. Training utilized NVIDIA GPUs with a batch size of 64 and Adam optimizer.

## Limitations

Performance depends on the quality of adjacent slices; small anomalies may be missed if slice correlation is weak.

## Advantages

Unsupervised approach eliminates the need for labeled data, making it scalable for anomaly detection in brain MRI.

## Applications

Anomaly detection in brain MRI for identifying tumors or abnormalities without manual annotations.

## Evaluation Metrics

Area Under the Curve (AUC), Sensitivity, Specificity.