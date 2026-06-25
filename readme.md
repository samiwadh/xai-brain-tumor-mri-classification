# NeuroScanAI

## Explainable Brain Tumor Classification Using CNN and EfficientNet

### Project Overview

NeuroScanAI is a deep learning project designed to classify brain MRI images into four categories:

* Glioma Tumor
* Meningioma Tumor
* Pituitary Tumor
* No Tumor

The project compares a Convolutional Neural Network (CNN) developed from scratch with a Transfer Learning approach based on EfficientNet. Model predictions are further interpreted using Grad-CAM visualizations to improve explainability and transparency.

---

## Motivation

Brain tumors are among the most critical neurological disorders, requiring accurate and timely diagnosis. Manual MRI interpretation is time-consuming and subject to human variability.

This project explores how deep learning can assist medical professionals by automatically identifying tumor types from MRI scans while providing visual explanations for predictions.

---

## Dataset

Brain Tumor MRI Dataset

Source:

Masoud Nickparvar (Kaggle)

Dataset Characteristics:

* 7023 MRI images
* 4 classes
* Pre-split training and testing sets

Classes:

1. Glioma
2. Meningioma
3. Pituitary
4. No Tumor

---

## Research Objectives

### Objective 1

Develop a CNN model for multi-class brain tumor classification.

### Objective 2

Evaluate whether transfer learning outperforms a CNN built from scratch.

### Objective 3

Analyze model explainability using Grad-CAM.

### Objective 4

Compare performance using:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

---

## Project Structure

NeuroScanAI/

├── data/

├── notebooks/

│   ├── 01_EDA.ipynb

│   ├── 02_CNN_Model.ipynb

│   ├── 03_EfficientNet_Model.ipynb

│   └── 04_GradCAM.ipynb

│

├── src/

├── reports/

├── results/

├── models/

├── requirements.txt

└── README.md

---

## Methodology

### Data Preprocessing

* Image resizing
* Normalization
* Data augmentation
* Train-validation split

### CNN Model

* Convolutional Layers
* ReLU Activation
* Max Pooling
* Dropout
* Fully Connected Layers

### Transfer Learning

EfficientNetB0 pretrained on ImageNet

* Frozen feature extractor
* Fine tuning
* Softmax classification head

### Explainability

Grad-CAM is used to visualize regions of MRI scans that influence model decisions.

---

## Technologies Used

Python

TensorFlow

Keras

NumPy

Pandas

Matplotlib

Scikit-Learn

OpenCV

---

## Evaluation Metrics

Accuracy

Precision

Recall

F1-Score

Confusion Matrix

Classification Report

---

## Results

| Model          | Accuracy |
| -------------- | -------- |
| CNN            | TBD      |
| EfficientNetB0 | TBD      |

Expected Performance:

CNN: 90-95%

EfficientNetB0: 95-99%

---

## Future Work

* MRI Segmentation
* Vision Transformers
* 3D CNN Models
* Clinical Validation
* Multi-modal Medical Imaging

---

## Author

Sami Wadho

MSc Data Science

University of Milano-Bicocca

Interests:

* Medical AI
* Deep Learning
* Computer Vision
* Explainable Artificial Intelligence

---

## License

This project is developed for educational and research purposes.
