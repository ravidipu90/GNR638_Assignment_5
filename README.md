# GNR638_Assignment_5
# Hierarchical Variational Autoencoder (HVAE) on UC Merced Land Use Dataset

This project implements a **Hierarchical Variational Autoencoder (HVAE)** to learn compact latent representations of satellite images from the [UC Merced Land Use Dataset](https://www.cs.ucmerced.edu/~gertner/courses/271/2018/project/UC_Merced_LandUse.zip). The model is built using TensorFlow and Keras, and trained in an unsupervised manner.

## 🧠 Model Overview

The HVAE has a two-level latent structure:

- **Latent Level 1 (z1)**: Encodes features with higher dimensionality (64).
- **Latent Level 2 (z2)**: Compresses z1 further into a more compact representation (32).

The encoder maps input images to the latent space via the **reparameterization trick**, and the decoder reconstructs images from `z2`. The loss includes reconstruction loss and two KL divergence terms (for `z1` and `z2`).

## 📂 Dataset

- **Name**: UC Merced Land Use Dataset
- **Images**: 2,100 aerial images (256x256 pixels)
- **Classes**: 21 land-use categories (e.g., agricultural, forest, residential, etc.)
- **Usage**: Only images are used for unsupervised learning (labels are ignored)

The dataset should be placed inside a folder named `data/`:agricultural/ ├── airplane/ ├── ...


## 🔧 Setup

### Dependencies

- Python 3.x
- TensorFlow 2.x
- NumPy
- Matplotlib

Install required packages:

```bash
pip install tensorflow numpy matplotlib

Prepare Dataset
Download and extract the UC Merced Dataset into the data/ directory.

Training
Train the HVAE using:

bash
Copy
Edit
python train.py
Image size: 64x64 (resized from 256x256)

Batch size: 32

Epochs: 30

Loss: MSE + KL divergence (z1 + z2)

The model uses ImageDataGenerator with a validation split of 20%.

 File Structure
bash
Copy
Edit
├── train.py             # Main training script
├── data/                # UC Merced dataset (organized by class folders)
├── assets/
│   └── loss_curve.png   # Generated after training
├── README.md            # Project documentation
✨ Key Features
Hierarchical latent space (z1 → z2)

Custom training loop with KL divergence tracking

Unsupervised learning with real-world aerial images

Modular encoder/decoder design

