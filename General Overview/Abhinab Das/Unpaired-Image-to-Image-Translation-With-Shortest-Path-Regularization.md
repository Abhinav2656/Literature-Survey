## Type of Paper
Research

## Authors
Chengyang Xie, Xuanhong Chen, Bingbing Ni, Kailing Guo, Lei Sun, Qi Liu, Pheng-Ann Heng

## Citation
C. Xie, X. Chen, B. Ni, K. Guo, L. Sun, Q. Liu, and P.-A. Heng, "Unpaired Image-to-Image Translation With Shortest Path Regularization," in *Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR)*, 2023, pp. 17875–17885, doi: [10.1109/CVPR52729.2023.01715](https://openaccess.thecvf.com/content/CVPR2023/papers/Xie_Unpaired_Image-to-Image_Translation_With_Shortest_Path_Regularization_CVPR_2023_paper.pdf).

## Description
This paper proposes a novel unpaired image-to-image translation method using shortest path regularization to improve translation quality in medical imaging.

## Methodology
Introduces a GAN-based framework with shortest path regularization to constrain latent space transitions, enhancing translation realism. Uses CycleGAN as the base model with additional regularization terms.

## Training & Dataset
Trained on unpaired MRI and CT datasets (e.g., IXI, internal datasets). Training used NVIDIA V100 GPUs with Adam optimizer.

## Limitations
Regularization complexity increases computational cost; may not generalize to all modalities.

## Advantages
Improves unpaired translation quality, making it suitable for scenarios with limited paired data.

## Applications
Unpaired medical image translation for cross-modality analysis.

## Evaluation Metrics
Fréchet Inception Distance (FID), Mean Absolute Error (MAE).