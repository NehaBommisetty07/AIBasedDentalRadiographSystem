# AI-Based Dental Radiograph Analysis System

## Overview

This project presents an **AI-powered dental radiograph analysis system** designed to classify abnormalities in dental images extracted from panoramic radiographs (OPG scans). The system uses deep learning techniques to automatically identify common dental conditions such as cavities, implants, fillings, and impacted teeth.

The model is trained using cropped tooth images and applies a **transfer learning approach with EfficientNet-B3** to achieve robust feature extraction and classification.

The goal of this system is to demonstrate how **Artificial Intelligence can support dental diagnostics and radiographic interpretation**, improving efficiency and assisting clinicians in identifying abnormalities.

---

## Problem Statement

Dental radiographs are routinely used to detect structural abnormalities and plan treatments. However, manual interpretation can be time-consuming and prone to inconsistencies.

This project aims to develop a deep learning model that can automatically analyze dental images and classify different dental conditions. Such systems can assist dentists by providing preliminary diagnostic insights.

---

## Objectives

The main objectives of this project are:

* Develop a deep learning model capable of classifying dental abnormalities
* Use **transfer learning** to improve model performance with limited datasets
* Build a scalable AI pipeline for dental radiograph analysis
* Provide a foundation for future systems that include segmentation and tooth numbering

---

## Classification Categories

The model classifies dental images into the following categories:

1. **Cavity**
2. **Fillings**
3. **Impacted Tooth**
4. **Implant**
5. **Normal**

These categories correspond to common clinical conditions visible in dental radiographs.

---

## Dataset Structure

The dataset consists of cropped dental radiograph images organized into training, validation, and test sets.

```
Segmented Dental Radiography/

train/
 ├── Cavity
 ├── Fillings
 ├── Impacted Tooth
 ├── Implant
 └── Normal

valid/
 ├── Cavity
 ├── Fillings
 ├── Impacted Tooth
 ├── Implant
 └── Normal

test/
 ├── Cavity
 ├── Fillings
 ├── Impacted Tooth
 ├── Implant
 └── Normal
```

Each folder contains radiographic images corresponding to the specific dental condition.

---

## Model Architecture

The system uses **EfficientNet-B3** as the backbone for feature extraction.

### Key Characteristics

* Pretrained on ImageNet
* Transfer learning based architecture
* Custom classification head
* Batch normalization and dropout for regularization

### Architecture Pipeline

```
Input Dental Image
       │
       ▼
EfficientNet-B3 Backbone
       │
       ▼
Fully Connected Layers
       │
       ▼
Softmax Classification
       │
       ▼
Predicted Dental Condition
```

---

## Data Preprocessing

The dataset undergoes several preprocessing and augmentation steps to improve model generalization.

### Image Processing

* Resize images to **224 × 224**
* Convert grayscale images to **RGB**
* Normalize using ImageNet statistics

### Data Augmentation

* CLAHE contrast enhancement
* Random brightness and contrast
* Random gamma correction
* Gaussian noise
* Horizontal flipping
* Shift, scale, and rotation transformations

These augmentations help the model learn robust features across varying radiograph conditions.

---

## Training Strategy

The model training follows a **two-stage transfer learning approach**.

### Stage 1 – Feature Extraction

* EfficientNet backbone is frozen
* Only the classification head is trained

### Stage 2 – Fine-Tuning (Optional)

* Backbone layers can be unfrozen
* The entire model is trained for improved performance

### Optimization

* Optimizer: Adam / AdamW
* Learning Rate Scheduler: Cosine Annealing
* Loss Function: Cross Entropy Loss

---

## Evaluation Metrics

The model performance is evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

These metrics help measure classification reliability across different dental conditions.

---

## Technologies Used

Programming Language
Python

Deep Learning Framework
PyTorch

Model Architecture
EfficientNet-B3

Libraries

* timm
* albumentations
* OpenCV
* NumPy
* scikit-learn
* matplotlib
* seaborn

Development Environment
Google Colab / GPU Runtime

---

## Running the Project

### 1. Mount Google Drive

```
from google.colab import drive
drive.mount('/content/drive')
```

### 2. Install Dependencies

```
pip install timm albumentations streamlit opencv-python pandas numpy
```

### 3. Train the Model

Run the training script inside the notebook or Python environment.

The model will load the dataset, perform preprocessing, and train the classifier.

---

## Expected Output

After training, the system will be able to:

* Classify dental images into five categories
* Provide evaluation metrics and confusion matrices
* Support future integration with full dental radiograph analysis pipelines

---

## Future Improvements

Possible future enhancements include:

* Tooth segmentation using U-Net or Mask R-CNN
* Automatic tooth numbering using the FDI system
* Full OPG analysis instead of cropped images
* Explainable AI visualization using Grad-CAM
* Clinical diagnostic dashboard using Streamlit

---

## Applications

* Dental radiograph analysis
* Automated dental condition classification
* Clinical decision support systems
* Dental education and training
* AI-assisted diagnostics

---

## Disclaimer

This system is developed for **educational and research purposes** and should not be used as a substitute for professional dental diagnosis.
