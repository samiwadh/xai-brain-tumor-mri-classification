# NeuroScanAI
### Explainable Brain Tumor MRI Classification Using EfficientNetB0 Transfer Learning

## Project Overview
NeuroScanAI is a deep learning project that classifies brain MRI images into four categories:
- Glioma Tumor
- Meningioma Tumor
- Pituitary Tumor
- No Tumor

The project uses EfficientNetB0 (transfer learning) as the classification model, and goes beyond standard accuracy reporting by adding Grad-CAM-based explainability and systematic misclassification analysis — examining not just *how accurate* the model is, but *whether it's looking at the right region* of the scan when it makes a prediction.

---
## Why Transfer Learning, Not a CNN From Scratch
Most public projects on this dataset train a CNN from scratch as a baseline, then compare it to a pretrained model. This project deliberately skips that step, for a concrete reason:

With only 1,400 images per class, a CNN trained from scratch has too little data to learn robust, generalizable features on its own — it tends to either underfit or overfit to dataset-specific noise. EfficientNetB0, pretrained on ImageNet, already encodes general low-level visual features (edges, textures, gradients) learned from millions of images. Transfer learning lets the model start from that strong foundation and adapt only a small classification head to this specific task — a more data-efficient and realistic approach given the dataset size.

Rather than reproducing the CNN-vs-transfer-learning comparison that most existing notebooks already show, this project uses the saved capacity to go deeper on a question fewer projects ask: **is the model's high accuracy actually trustworthy, or is it relying on the wrong visual cues?** That's the role Grad-CAM plays here.

---
## Motivation
Brain tumors are among the most critical neurological disorders, requiring accurate and timely diagnosis. Manual MRI interpretation is time-consuming and subject to human variability. This project explores how deep learning can assist medical professionals by automatically identifying tumor types from MRI scans — while also providing visual evidence for *why* the model made each prediction, since unexplained predictions have limited clinical value.

---
## Dataset
**Brain Tumor MRI Dataset**
Source: Masoud Nickparvar (Kaggle)
- 7,023 MRI images
- 4 classes, balanced
- Pre-split training and testing sets, no leakage between them

Classes: Glioma, Meningioma, Pituitary, No Tumor

---
## Research Objectives
**Objective 1** — Develop an EfficientNetB0 transfer-learning model for multi-class brain tumor classification.

**Objective 2** — Evaluate per-class performance (precision, recall, F1), not just overall accuracy, since error types matter differently in a medical context.

**Objective 3** — Apply Grad-CAM to visualize which MRI regions drive each prediction, and identify whether the model focuses on the tumor or on irrelevant artifacts.

**Objective 4** — Conduct a systematic misclassification analysis: identify which class-pairs are confused most often and examine their Grad-CAM heatmaps for an explanation.



---
## Methodology
**Data Preprocessing**
- Image resizing to 224×224 (EfficientNetB0 input size)
- Normalization (pixel rescaling)
- Data augmentation (rotation, zoom, horizontal flip) on training data only
- Train/validation split with no leakage into the test set

**Transfer Learning Model**
- EfficientNetB0 pretrained on ImageNet
- Frozen feature extractor
- Custom classification head: GlobalAveragePooling → Dropout → Dense(128, ReLU) → Dense(4, Softmax)
- EarlyStopping and ReduceLROnPlateau to prevent overfitting

**Explainability**
- Grad-CAM (Gradient-weighted Class Activation Mapping) applied to the model's final convolutional layer
- Heatmaps overlaid on original MRI scans to show prediction-driving regions
- Misclassified samples specifically reviewed for explainability patterns

---
## Technologies Used
Python, TensorFlow, Keras, NumPy, Matplotlib, Scikit-learn, OpenCV

---
## Evaluation Metrics
Accuracy, Precision, Recall, F1-Score, Confusion Matrix, Classification Report

---
## Results
| Model          | Accuracy |
|----------------|----------|
| EfficientNetB0 | 92.62%   |

Glioma recall (0.75) is the weakest per-class metric; the dominant error is glioma misclassified as meningioma (65 of 118 total test errors). Notumor and pituitary are classified with zero errors. See the full report for the Grad-CAM misclassification analysis.

---
## Future Work
- MRI tumor segmentation (U-Net)
- Vision Transformer comparison
- Domain-shift testing across different MRI sources
- Clinical validation with radiologist review

---
## Author
**Abdul Sami **
MSc Data Science, University of Milano-Bicocca
Interests: Medical AI, Deep Learning, Computer Vision, Explainable AI

---
## License
Developed for educational and research purposes
