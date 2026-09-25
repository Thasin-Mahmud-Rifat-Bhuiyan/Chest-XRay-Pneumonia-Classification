# Chest X-Ray Pneumonia Classification

A computer vision project for classifying pediatric chest X-ray images into three categories: **Normal, Bacterial Pneumonia, and Viral Pneumonia** using **MobileNetV2 transfer learning**.

## Overview

This project focuses on developing a deep learning model for multi-class classification of pediatric chest X-ray images.

The model classifies each X-ray image into one of the following categories:

* Normal
* Bacterial Pneumonia
* Viral Pneumonia

The project follows a complete computer vision workflow, including data loading, data analysis, image preprocessing, augmentation, transfer learning, model training, evaluation, and visualization.

## Dataset

The project uses a chest X-ray dataset containing pediatric X-ray images.

The dataset is divided into:

* Training set
* Testing set

The original training data is further divided into:

* 80% Training
* 20% Validation

The final test set is kept separate for model evaluation.

### Classes

| Class    | Description         |
| -------- | ------------------- |
| NORMAL   | Normal chest X-ray  |
| BACTERIA | Bacterial pneumonia |
| VIRUS    | Viral pneumonia     |

The notebook loads **5,232 training images** and **624 test images** from the dataset used in the project.

## Technologies Used

* Python
* TensorFlow
* Keras
* OpenCV
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Scikit-learn

## Model

This project uses **MobileNetV2** with transfer learning.

The pretrained MobileNetV2 base is used as a feature extractor, followed by a custom classification head.

### Model Architecture

```text
Input Image
     ↓
224 × 224 × 3
     ↓
MobileNetV2
     ↓
Global Average Pooling
     ↓
Dense Layer (128)
     ↓
Dropout (0.5)
     ↓
Softmax Output
     ↓
Normal / Bacterial / Viral
```

The MobileNetV2 base layers are initially frozen and the custom classification layers are trained for the three target classes.

## Image Preprocessing

The images are processed using the following techniques:

* Resize to 224 × 224 pixels
* Pixel normalization to the range [0, 1]
* Rotation augmentation
* Horizontal flipping
* Zoom augmentation

Data augmentation is applied only to the training data.

Validation and test images are only normalized without augmentation.

## Handling Class Imbalance

Class weights are calculated using the training data to reduce the effect of class imbalance.

This helps prevent the model from becoming overly biased toward classes with more training samples.

## Training

The model is compiled using:

* Optimizer: Adam
* Loss Function: Categorical Crossentropy
* Metric: Accuracy

Training also uses:

* Early Stopping
* Reduce Learning Rate on Plateau
* Class Weights

The model is trained for up to 15 epochs.

## Evaluation

The model is evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Classification Report
* Confusion Matrix

The project also analyzes class-wise performance and specifically examines confusion between bacterial and viral pneumonia.

## Visualization

The notebook includes several visualizations:

* Class distribution
* Sample chest X-ray images
* Training vs validation accuracy
* Training vs validation loss
* Confusion matrix
* Correct predictions
* Misclassified predictions
* Prediction confidence

## Project Workflow

```text
Dataset
   ↓
Data Loading
   ↓
Data Understanding
   ↓
Class Distribution Analysis
   ↓
Train / Validation Split
   ↓
Image Resizing
   ↓
Normalization
   ↓
Data Augmentation
   ↓
Class Weight Calculation
   ↓
MobileNetV2 Transfer Learning
   ↓
Model Training
   ↓
Validation
   ↓
Test Evaluation
   ↓
Accuracy / Precision / Recall / F1-score
   ↓
Confusion Matrix
   ↓
Class-wise Analysis
   ↓
Prediction Visualization
```

## Results

The model's performance is evaluated on the separate test dataset.

The notebook reports the final:

* Test Accuracy
* Precision
* Recall
* F1-score
* Class-wise performance
* Confusion matrix

The training history is also visualized to compare training and validation performance.

## Limitations

This project is intended for educational and research purposes and should not be considered a medical diagnostic system.

The dataset consists of pediatric chest X-ray images, so the model may not generalize to adult patients or images from different hospitals and imaging devices.

Bacterial and viral pneumonia can have similar visual characteristics, which may cause classification errors.

Further validation using larger and more diverse datasets would be required before considering real-world clinical applications.

## Repository Structure

```text
Chest-XRay-Pneumonia-Classification/
│
├── hirl-final.ipynb
└── README.md
```

## Disclaimer

This project is developed for academic and educational purposes. It is not intended to replace professional medical diagnosis or clinical decision-making.
