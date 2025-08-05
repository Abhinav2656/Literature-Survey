## Type of Paper
Research

## Authors
Yiwen Chen, Zixuan Chen, Xiaolei Huang, Yuexiang Li

## Citation
Y. Chen, Z. Chen, X. Huang, and Y. Li, "Versatile Medical Image Segmentation Learned from Multi-Source Datasets via Model Self-Disambiguation," in *Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR)*, 2024, pp. 17765–17774, doi: [10.1109/CVPR52729.2024.01705](https://openaccess.thecvf.com/content/CVPR2024/papers/Chen_Versatile_Medical_Image_Segmentation_Learned_from_Multi-Source_Datasets_via_Model_CVPR_2024_paper.pdf).

## Description
This paper proposes a weakly-supervised segmentation model using 3D TransUNet, leveraging multi-source datasets with self-disambiguation for improved performance.

## Methodology
Uses 3D TransUNet as the base network, incorporating a self-disambiguation module to handle multi-source data inconsistencies. Employs adversarial training for robustness.

## Training & Dataset
Trained on multi-source datasets (e.g., BraTS, MSD). Training used NVIDIA V100 GPUs with a hybrid loss function.

## Limitations
Weakly-supervised approach may miss fine details compared to fully supervised methods.

## Advantages
Handles diverse datasets effectively, improving generalizability in segmentation tasks.

## Applications
Weakly-supervised segmentation for multi-modal medical imaging.

## Evaluation Metrics
Dice Similarity Coefficient (DSC), Hausdorff Distance (HD).