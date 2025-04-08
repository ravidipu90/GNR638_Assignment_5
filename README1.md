
# Hierarchical Variational Autoencoder (HVAE) on UC Merced Land Use Dataset
### Dataset: UC Merced Land Use Dataset

---

## 1. Introduction

This project implements a **Hierarchical Variational Autoencoder (HVAE)** for **unsupervised image representation learning**. HVAE is an extension of the traditional VAE that introduces multiple levels of latent variables, enabling the model to learn more structured and abstract features. The model is trained on the **UC Merced Land Use Dataset**, a collection of aerial land-use images categorized into 21 classes.

---

## 2. Dataset

- **Dataset**: [UC Merced Land Use Dataset](https://visions.eng.ucmerced.edu/dataset/landuse.html)
- **Classes**: 21 (e.g., agricultural, forest, river, freeway, etc.)
- **Images per class**: 100
- **Image size**: 256×256 pixels
- **Preprocessing**:
  - Resized to 64×64
  - Normalized to [0, 1] range
  - Split: 80% Training / 20% Validation

---

## 3. Objective

To learn a hierarchical latent representation of images using a two-level latent structure and evaluate the model based on reconstruction loss and KL divergence. The learned embeddings can be further used for clustering, visualization, or downstream tasks like land use classification.

---

## 4. Methodology

### 4.1 Model Architecture

#### Encoder
- Convolutional layers extract hierarchical features.
- Two levels of latent variables:
  - **Level 1 (z1)**: Dimension = 64
  - **Level 2 (z2)**: Dimension = 32
- Uses the **reparameterization trick** for both z1 and z2.

#### Decoder
- Takes `z2` and reconstructs the image using transposed convolutions.
- Final activation: **Sigmoid** for normalized image output.

### 4.2 HVAE Loss Function
- **Reconstruction Loss**: Mean Squared Error (MSE)
- **KL Divergence Loss**:
  - For `z1` and `z2` against standard normal distributions
- **Total Loss** = Reconstruction Loss + KL(z1) + KL(z2)

---

## 5. Training Setup

- **Epochs**: 30  
- **Batch size**: 32  
- **Optimizer**: Adam  
- **Framework**: TensorFlow / Keras  
- **Hardware**: GPU Recommended  

---

## 6. Results

### 6.1 Loss Curves
The training and validation loss curves are plotted to observe model convergence. The figure shows how the model gradually reduces both reconstruction and KL divergence losses.

![Loss Curve Placeholder]

### 6.2 Reconstruction
The decoder effectively reconstructs input images from their hierarchical latent embeddings, showing the model's ability to capture high-level semantics.

---

## 7. Applications

- **Dimensionality Reduction**
- **Feature Learning for Land Use Classification**
- **Image Clustering and Retrieval**
- **Generative Sampling of Synthetic Satellite Images**

---

## 8. Future Work

- Visualize the latent space using **t-SNE or UMAP**
- Perform **clustering** on latent vectors to evaluate separability
- Extend to **semi-supervised classification**
- Use **contrastive learning** on top of the HVAE backbone

---

## 9. Conclusion

The HVAE model efficiently learns hierarchical latent representations of land-use images. It captures complex structures via stacked latent variables and performs robust unsupervised training. This project lays the foundation for using generative models in remote sensing and aerial image understanding.
