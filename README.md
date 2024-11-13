# Bone Fracture Classification Using Transfer Learning

This project applies deep learning techniques to classify bone fractures in X-ray images. Using a ResNet18 model pretrained on ImageNet, the model is fine-tuned to distinguish between fractured and non-fractured bones. The model uses PyTorch and transfer learning techniques for binary classification.

![Confusion Matrix](output.png)

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Data Preprocessing](#data-preprocessing)
- [Training](#training)
- [Evaluation](#evaluation)
- [Installation and Setup](#installation-and-setup)
- [Usage](#usage)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [References](#references)

---

## Overview
This project addresses the problem of classifying X-ray images as fractured or not fractured. By leveraging transfer learning with a pretrained ResNet18, the model learns features specific to fractures in bones, achieving high accuracy on the dataset.

## Dataset
The dataset is organized into three folders:
- `train`: Training data
- `val`: Validation data
- `test`: Test data

Each folder has two subdirectories:
- `fractured`: Images of fractured bones.
- `not fractured`: Images of non-fractured bones.

The dataset folder structure:


## Model Architecture
- **Base Model**: ResNet18 pretrained on ImageNet.
- **Modified Layers**: The fully connected (FC) layer is replaced with a custom FC layer:
  - `Linear(num_features, 256)`
  - `ReLU`
  - `Dropout(0.5)`
  - `Linear(256, 1)`
  - `Sigmoid` (for binary classification)

The pretrained layers are frozen, and only the new FC layers are trained.

## Data Preprocessing
- **Transformations**:
  - **Training Data**: Resize, random horizontal flip, random rotation, random crop, normalization.
  - **Validation/Test Data**: Resize, normalization.
  
These augmentations improve model generalization and avoid overfitting.

## Training
- **Loss Function**: Binary Cross-Entropy Loss (`BCELoss`)
- **Optimizer**: Adam optimizer with learning rate `0.001`
- **Scheduler**: Learning rate scheduler to reduce LR by a factor of `0.1` every 5 epochs.
- **Early Stopping**: Implemented to prevent overfitting by stopping training when validation loss stops improving.

## Evaluation
The model evaluation includes:
1. **Accuracy** on the test set.
2. **Classification Report**: Precision, recall, and F1-score for each class.
3. **Confusion Matrix** to visualize the performance of each class.

## Installation and Setup
1. **Clone the repository**:
    ```bash
    git clone https://github.com/your_username/bone-fracture-classification.git
    cd bone-fracture-classification
    ```

2. **Install Dependencies**:
    Make sure you have Python 3.7+ and install required packages:
    ```bash
    pip install -r requirements.txt
    ```
    Required packages include `torch`, `torchvision`, `scikit-learn`, `Pillow`, and `matplotlib`.

3. **Dataset**:
    Place the dataset in the `Bone_Fracture_Binary_Classification` directory as shown above.

## Usage

### 1. Training the Model
To train the model, use the following command:
```python
python train.py
