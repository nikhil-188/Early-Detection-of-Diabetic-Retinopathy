# Early Stage of Diabetic Retinopathy in Retinal Images Using Efficient Dense Net

**Problem Identification**
Diabetic Retinopathy (DR) is a leading cause of blindness if not detected early.
Manual screening of retinal fundus images is time-consuming and subjective.
The goal was to build an automated deep learning–based system to accurately classify DR severity, with special focus on early-stage detection.

**Dataset Collection**
Used a labeled retinal fundus image dataset.
Images were categorized into five DR severity classes:
No DR
Mild
Moderate
Severe
Proliferative DR
Dataset contained variations in illumination, noise, and image quality.

**Baseline CNN Setup**
A basic CNN architecture was first implemented.
Purpose:
Establish a baseline
Objectively evaluate preprocessing techniques without bias from advanced models

**Preprocessing Technique Experimentation**
Multiple image preprocessing techniques were applied individually on the baseline CNN:
Gaussian Blurring
Canny Edge Detection
CLAHE
Adaptive Histogram Equalization (AHE)
Local Ternary Patterns (LTP)

**Selection of Optimal Preprocessing**
Model performance was compared across all preprocessing methods.
Gaussian Blurring consistently produced the best results.
Reason:
Reduced noise
Preserved critical retinal features like microaneurysms and hemorrhages
Decision: Gaussian Blurring chosen as the final preprocessing method for all further experiments.

**Training Advanced Deep Learning Models**
With Gaussian Blurring applied, multiple CNN architectures were trained:
CNN
ResNet-50
DenseNet-121
MobileNet-V2
EfficientNet-B5

**Model Benchmarking**
All architectures were evaluated using:
Accuracy
Precision
Recall
F1-score
ROC-AUC
Comparative analysis was performed to identify top-performing models.

**Identification of Top Models**
EfficientNet-B5 and DenseNet-121 consistently outperformed other architectures.
These models demonstrated better feature extraction and classification capability for DR severity.

**Motivation for Hybrid Model**
Single models showed strong performance but had limitations.
A hybrid approach was proposed to:
Combine EfficientNet-B5’s efficient global feature extraction
With DenseNet-121’s dense feature reuse and gradient flow

**Hybrid Model Design (Model Chaining)**
EfficientNet-B5 was used as Model 1:
Fully connected layers were removed
Used purely as a feature extractor
DenseNet-121 was used as Model 2:
Receives feature representations
Further refines features using dense connectivity

**Feature-Level Fusion**
Features extracted from EfficientNet-B5 and DenseNet-121 were concatenated.
This is feature-level fusion, not ensemble averaging.
The combined feature vector represents complementary learned information.

**Final Classification**
The fused feature vector was passed to a final fully connected output layer.
The model predicted one of the five DR severity classes.

**Results**
The proposed hybrid EfficientNet-B5 + DenseNet-121 model:
Achieved 89% classification accuracy
Outperformed all individual architectures
Showed improved performance for early-stage DR detection

