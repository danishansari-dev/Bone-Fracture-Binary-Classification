# Bone Fracture Classification using Transfer Learning (ResNet18)

## Table of Contents
1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Model Architecture](#model-architecture)
4. [Data Preprocessing](#data-preprocessing)
5. [Training and Early Stopping](#training-and-early-stopping)
6. [Evaluation and Results](#evaluation-and-results)
7. [Installation](#installation)
8. [Usage](#usage)
9. [Future Improvements](#future-improvements)
10. [Contributing](#contributing)

---

## Project Overview
This project is a binary classification model designed to detect bone fractures in X-ray images using deep learning. By leveraging transfer learning on a pre-trained ResNet18 model, the model achieves a robust performance on this task, making it suitable for assisting radiologists in identifying fractures.

## Dataset
- **Classes**: Fractured, Not Fractured
- **Directory Structure**:
  - `train`: Training set images.
  - `val`: Validation set images.
  - `test`: Test set images.


## Model Architecture
The model is based on **ResNet18**, pre-trained on ImageNet, and fine-tuned for binary classification:
- **Frozen Layers**: All layers except the final fully connected layers.
- **Modified Output Layer**: Adjusted to a binary classification with sigmoid activation.

## Data Preprocessing
Data augmentation and normalization are applied to improve model generalization:
- **Training**: Resize to 224x224, Random Horizontal Flip, Random Rotation (10°), Random Resized Crop, Normalize.
- **Validation/Test**: Resize to 224x224, Normalize.

## Training and Early Stopping
Training uses **Binary Cross Entropy Loss** and **Adam Optimizer** with a learning rate scheduler:
- **Early Stopping**: Prevents overfitting by monitoring validation loss and stopping training if no improvement is seen after several epochs.

## Evaluation and Results

### Key Performance Metrics:
- **Accuracy**: 86.76% on the test set
- **Classification Report**:

                     precision    recall  f1-score   support

          fractured       0.86      0.91      0.88       238
      not fractured       0.92      0.87      0.89       268

           accuracy                           0.89       506
          macro avg       0.89      0.89      0.89       506
       weighted avg       0.89      0.89      0.89       506




- **Confusion Matrix**:

![Confusion Matrix](output.png)  <!-- Update with the correct path to confusion matrix image -->


### Sample Prediction Output:
[Predicted Image](predicted.png)


   


