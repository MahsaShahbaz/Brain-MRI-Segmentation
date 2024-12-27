# Brain MRI Segmentation

This repository provides an implementation for analyzing and segmenting brain MRI images using the LGG (Low-Grade Glioma) Segmentation Dataset. This dataset includes brain MR images along with manual FLAIR abnormality segmentation masks, sourced from The Cancer Imaging Archive (TCIA).

## Dataset Overview

The LGG Segmentation Dataset contains:

- **Brain MRI Images**: Medical images captured using FLAIR (Fluid-Attenuated Inversion Recovery) sequences.
- **Segmentation Masks**: Manually annotated masks highlighting abnormalities, such as tumor regions, in the MRIs.
- **Clinical Data**: Includes tumor genomic clusters and patient information in the accompanying `data.csv` file.

### Source
The dataset is based on research publications:
- *Mateusz Buda, Ashirbani Saha, Maciej A. Mazurowski*: "Association of genomic subtypes of lower-grade gliomas with shape features automatically extracted by a deep learning algorithm." (*Computers in Biology and Medicine*, 2019).
- *Maciej A. Mazurowski et al.*: "Radiogenomics of lower-grade glioma: algorithmically-assessed tumor shape is associated with tumor genomic subtypes and patient outcomes in a multi-institutional study with The Cancer Genome Atlas data." (*Journal of Neuro-Oncology*, 2017).

For additional details, refer to the genomic data publication:
- ["Comprehensive, Integrative Genomic Analysis of Diffuse Lower-Grade Gliomas"](https://www.nejm.org/doi/full/10.1056/NEJMoa1402121)

### Key Dataset Details
- Images correspond to 110 patients with TCGA lower-grade gliomas.
- Provides insights into genomic subtypes, tumor shape, and patient outcomes.

## Features of this Repository

- **Preprocessing**:
  - Handles loading and preprocessing of MRI scans and corresponding segmentation masks.
  - Includes normalization and data augmentation techniques like flipping, rotation, and cropping to improve model generalization.
  - Prepares data for training using `ImageDataGenerator` for on-the-fly image preprocessing and batching.

- **Deep Learning Models**:
  - Implements:
    - **ResNet50** as a backbone for classification of images with and without tumors.
    - **ResUNet** architecture for tumor segmentation, combining residual blocks and U-Net-style upsampling.
  - Custom residual block implementation to enhance feature extraction.
  - Uses advanced loss functions such as **Focal Tversky Loss** to handle imbalanced datasets effectively.
  - Integrates learning rate scheduling, early stopping, and model checkpoints for optimal training.

- **Visualization**:
  - Provides tools to visualize MRI scans, segmentation masks, and model predictions.
  - Side-by-side visualization of original MRI, ground truth masks, and predicted masks.
  - Includes detailed plots of performance metrics like confusion matrices and classification reports.

- **Analysis**:
  - Evaluates model performance using metrics like Dice Coefficient, Intersection over Union (IoU), and classification accuracy.
  - Analyzes and compares AI-predicted masks with ground truth annotations.
  - Generates detailed reports to highlight model strengths and areas for improvement.

- **Utilities**:
  - Custom utility scripts for data generators, loss functions, and post-processing predictions.
  - Tools to save and reload model architectures and weights for reproducibility.


## Prerequisites

- Python 3.x
- Required libraries:
  - `numpy`, `pandas`, `tensorflow`, `cv2`, `skimage`, `matplotlib`
