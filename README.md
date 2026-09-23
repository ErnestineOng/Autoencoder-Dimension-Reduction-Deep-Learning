# 🖼️ Image Dimension Reduction Using Autoencoder

A Deep Learning project that applies an **Autoencoder** to reduce the dimensionality of overhead imagery while preserving important visual information. The project compares a baseline Autoencoder with modified and tuned architectures using the **Overhead-MNIST Plane dataset**.

## 🎯 Project Overview

The objective is to compress **28×28 grayscale images (784 pixels)** into a **128-dimensional latent representation**, then reconstruct the original images from the compressed representation.

The reconstruction quality is evaluated using **Structural Similarity Index (SSIM)**.

## 📊 Dataset

The dataset is taken from **Overhead-MNIST** and uses the **Plane** class.

* Class: Plane
* Total images: 1,000
* Image size: 28 × 28 pixels
* Original dimension: 784
* Reduced dimension: 128
* Pixel values normalized to [0, 1]

The data is divided into:

* 80% Training
* 10% Validation
* 10% Testing

## 🔧 Methodology

### Baseline Autoencoder

The baseline architecture reduces the 28×28 input into a **128-dimensional latent space** and reconstructs it back into the original image dimensions.

### Modified Autoencoder (v2)

The architecture was improved by:

* Increasing Conv2D filters from 32 to 64
* Adding a Dense layer with 256 neurons before the latent layer
* Applying L2 regularization
* Replacing MSE loss with **SSIM Loss**

These changes aim to improve the preservation of image structure during reconstruction.

### Tuned Autoencoder (v3)

The final architecture applies additional hyperparameter tuning:

* Cosine Decay learning rate
* Initial learning rate: 3e-4
* Final learning rate: 1e-5
* Batch size: 32
* Maximum epochs: 150
* Dropout: 5%
* Early Stopping

## 📈 Results

| Model       |  Mean SSIM | Std SSIM | Test MSE |
| ----------- | ---------: | -------: | -------: |
| Baseline    |     0.5811 |   0.1610 | 0.020326 |
| Modified v2 |     0.5919 |   0.1647 | 0.030185 |
| Tuned v3    | **0.6123** |   0.1515 | 0.027088 |

The final tuned model achieved a Mean SSIM of **0.6123**, an improvement of **0.0312** compared with the baseline.

The improvement indicates that the modified architecture and hyperparameter tuning helped the model preserve more structural information during image reconstruction.

## 💡 Key Findings

* Autoencoders can compress 784-dimensional image data into a 128-dimensional latent representation.
* Using SSIM Loss helps the model focus more on structural similarity between the original and reconstructed images.
* Increasing the convolutional capacity and adding regularization improved the reconstruction quality.
* Hyperparameter tuning with Cosine Decay, smaller batch size, and dropout further improved the Mean SSIM.

## 🛠️ Tools & Technologies

* Python
* TensorFlow / Keras
* NumPy
* Matplotlib
* Scikit-learn
* scikit-image
* Jupyter Notebook


## 📚 Dataset Source

Overhead-MNIST Dataset:
https://www.kaggle.com/datasets/datamunge/overheadmnist/data

Dataset paper:
https://arxiv.org/pdf/2102.04266

## 📝 Project Type

**Deep Learning — Autoencoder & Dimension Reduction**

Task: Dimension Reduction of Overhead Imagery
Dataset: Overhead-MNIST — Plane
