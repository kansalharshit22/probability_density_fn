
# Learning Probability Density Function using GAN

## Overview
This project focuses on learning the probability density function (PDF) of a transformed random variable using a Generative Adversarial Network (GAN).

Instead of assuming any predefined parametric distribution (e.g., Gaussian or Exponential), the model learns the underlying distribution directly from observed data samples. The objective is to demonstrate how GANs can approximate complex probability distributions purely through adversarial learning.

---

## Dataset
- Source: India Air Quality Dataset (Kaggle)
- Feature used: NO₂ concentration

---

## Step 1: Transformation
For roll number **102303554**:

a_r = 1.5  
b_r = 1.5  

Transformation applied:
z = x + 1.5 sin(1.5x)

---

## Step 2: GAN Model
Generator:
- Input: 1D Gaussian noise
- Layers: 1 → 64 → 32 → 1
- Activation: LeakyReLU

Discriminator:
- Input: 1D sample
- Layers: 1 → 64 → 32 → 1
- Output: Real/Fake probability

Training:
- Loss: Binary Cross Entropy
- Optimizer: Adam
- Epochs: 2500
- Batch Size: 128

---

## Step 3: PDF Estimation
- Generate large samples from trained generator
- Apply Kernel Density Estimation (KDE)
- Compare with histogram of real transformed data

---

## Observations
- GAN successfully captures dominant modes of the transformed distribution.
- Training remains stable without significant mode collapse.
- Generated samples closely follow the statistical characteristics of real data.
- KDE visualization shows strong alignment between learned and actual PDFs.

---

## Conclusion
The GAN effectively learns an unknown probability distribution using only sample data, demonstrating that adversarial learning can be used as a non-parametric density estimation technique.
This approach is useful when analytical forms of distributions are unknown or difficult to model.
