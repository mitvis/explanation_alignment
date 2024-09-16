# Explanation Alignment Experiments

This repository contains the code and instructions for reproducing the experiments from the paper:

**"Explanation Alignment: Quantifying the Correctness of Model Reasoning At Scale"**  
by Hyemin Bang, Angie Boggust, and Arvind Satyanarayan from MIT CSAIL.

## Overview

The goal of this repository is to compute **explanation alignment**, which measures the alignment between machine learning models' saliency-based explanations and human explanations. The experiments utilize various model architectures and saliency methods across datasets like MNIST, CelebA, and ImageNet.

### Key Contributions:
- Introduces **explanation alignment** to assess whether model predictions are made for the right reasons.
- Uses **Shared Interest** and **Pointing Game** as saliency-based alignment metrics.
- Evaluates models on biases, spurious correlations, and behavioral differences.

## Requirements:
To run the experiments, you will need to download the following datasets:
- ImageNet
- CelebA (https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)
- CelebAMask-HQ (https://mmlab.ie.cuhk.edu.hk/projects/CelebA/CelebAMask_HQ.html)
- MNIST

## Reproducing Key Experiments

### 1. MNIST Spurious Correlation Detection
To reproduce the experiment on detecting spurious correlations in MNIST:
- Run the `mnist_spurious_experiment.ipynb` notebook.
- This notebook introduces a spurious correlation (e.g., a colored square) in the MNIST dataset and trains two models:
  - One that learns the correct correlation (digit classification)
  - One that learns the spurious correlation (color-box)

### 2. CelebA Bias Detection
To detect bias in smile prediction using the CelebA dataset:
- Run the `celeba_bias_experiment.ipynb` notebook.
- This notebook evaluates the model’s reliance on biased features (e.g., hair color) when predicting smiles:
  - One model learns unbiased features (mouth region)
  - Another model relies on biased features (hair color)

### 3. CelebA-HQ Mask Feature Ranking
To evaluate model alignment with different face regions using CelebA-HQ masks:
- Run the `celeba_mask_feature_ranking.ipynb` notebook.
- This notebook ranks the model's reliance on various facial features (hair, eyes, mouth, etc.) by computing saliency map alignment:
  - It uses GradCAM saliency method to evaluate regions like the mouth, nose, eyes, etc.
  - Multiple human explanations are compared with model saliency maps.

### 4. CIFAR-100 Transfer Learning
To test the transferability of explanation alignment from ImageNet models to CIFAR-100:
- Run the `cifar100_transfer_learning.ipynb` notebook. 
- This notebook evaluates how well ImageNet-trained models generalize to CIFAR-100 in a 1-shot learning task:
  - It measures how transferable the model’s explanations are across different datasets and tasks.
  - The explanation alignment scores are used to assess generalization performance.

### 5. ImageNet Model Comparison
To compare explanation alignment across multiple ImageNet models:
- Run the `imagenet_model_comparison.ipynb` notebook to compute explanation alignment for a variety of pre-trained ImageNet models.
- This notebook evaluates the alignment of model saliency maps with human explanations on the ImageNet validation set.