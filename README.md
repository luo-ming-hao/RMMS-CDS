# RMMS-CDS

**RMMS-CDS: A Decision-Support Diagnostic System for Scoliosis Assessment from Spinal X-rays**

## Overview

RMMS-CDS is a deep learning-based framework developed for automated spinal X-ray segmentation and computer-assisted scoliosis assessment.

The framework addresses challenges associated with spinal radiographic imaging, including low contrast, variable exposure, overlapping anatomical structures, and limited annotated training data.

By integrating image preprocessing, structure-preserving data augmentation, and multi-scale residual learning, RMMS-CDS aims to improve spinal segmentation accuracy and support downstream quantitative scoliosis assessment, including end-vertebra localization and Cobb angle measurement.

## Framework

RMMS-CDS consists of three main components:

### 1. Spine-ROI Prep

A preprocessing module designed to improve image consistency and focus on relevant anatomical regions.

- Quantile-based intensity truncation
- Intensity normalization
- Coarse spinal region localization
- Region-of-interest (ROI) cropping

### 2. Spine-MC Augmentation

A Monte Carlo-based data augmentation strategy designed to increase training diversity while preserving anatomical structures.

- Monte Carlo sampling
- Multiple image augmentation operators
- Anatomical constraint filtering
- Structure-preserving sample generation

### 3. MSRNet

A multi-scale residual segmentation network developed to extract spinal structures from X-ray images.

The network incorporates:

- Residual learning
- Multi-scale convolution
- Context Enhancement Module (CEM)
- Dilated convolution pyramid
- Multi-scale feature fusion

## Experimental Results

The proposed framework was evaluated on spinal X-ray images using segmentation and clinical assessment metrics.

### Spinal Segmentation

| Metric | Result |
|---|---|
| Intersection over Union (IoU) | 75.51% |
| Dice Similarity Coefficient (DSC) | 86.06% |
| Precision | 85.53% |
| Recall | 86.61% |
| Accuracy | 92.87% |

### Clinical Endpoint Evaluation

| Clinical Task | Result |
|---|---|
| Upper End-Vertebra Detection Accuracy | 87.36% |
| Lower End-Vertebra Detection Accuracy | 86.42% |
| Both End-Vertebrae Detection Accuracy | 78.15% |
| Cobb Angle MAE | 4.37° |
| Cobb Angle RMSE | 6.18° |

Clinical assessment results were evaluated against expert reference annotations and manual measurements established by two orthopedic physicians.

These findings indicate the potential of RMMS-CDS to support quantitative scoliosis assessment beyond pixel-level segmentation.

## Experimental Configuration

The main experimental settings are summarized below.

| Parameter | Configuration |
|---|---|
| Deep Learning Framework | PyTorch |
| GPU | NVIDIA RTX 4090 |
| Input Image Size | 1084 × 2437 |
| Optimizer | Adam |
| Initial Learning Rate | 4 × 10⁻⁵ |
| Learning Rate Scheduler | Cosine Annealing |
| Training Epochs | 100 |
| Batch Size | 12 |
| Loss Function | 0.5 × Dice Loss + 0.5 × Binary Cross-Entropy Loss |
| Random Seed | 11 |
| Data Split | 70% Training / 20% Validation / 10% Testing |

## Cross-Modal Evaluation

In addition to spinal X-ray segmentation, the proposed framework was evaluated on two additional medical image segmentation datasets:

- Prostate tumor MRI: 768 images
- Liver tumor CT: 1,854 images

These experiments investigate the applicability of the segmentation framework across different anatomical structures and imaging modalities. They are supplementary evaluations and do not constitute clinical validation for scoliosis assessment.

## Repository Contents

This repository is intended to provide the implementation of RMMS-CDS and supporting materials for reproducibility.

The main components include:

- MSRNet network architecture
- Spine-ROI Prep preprocessing
- Spine-MC Augmentation
- Model training and evaluation procedures
- Clinical endpoint evaluation utilities
- Experimental configuration files


## Dataset Availability

The original spinal X-ray dataset was collected from a hospital and is currently subject to a commercial embargo.

The dataset is not publicly available at present. Requests for access may be considered by the corresponding author 12 months after publication, subject to applicable restrictions.

No patient imaging data are included in this repository.


