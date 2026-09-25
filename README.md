# Multimodal Deep Learning System for Detecting Respiratory Diseases Using Lung Imaging and Respiratory Audio

##  Overview

This project presents a **multimodal deep learning framework for respiratory disease detection** by combining two important diagnostic modalities:

*  Lung imaging
* 🎙️Respiratory audio

The system is designed to analyze complementary information from lung images and respiratory sounds to support the detection of respiratory diseases.

The proposed framework focuses on the classification of:

* Normal
* Pneumonia
* Tuberculosis

The project combines **ResNet50-based image analysis** with a **CNN + Transformer-based audio analysis pipeline**. Explainable AI techniques, including **Grad-CAM** and **Transformer attention**, are also incorporated to provide qualitative explanations for model predictions.

---

##  Objectives

The main objectives of this project are:

1. To develop a multimodal deep learning framework for respiratory disease detection.
2. To analyze structural abnormalities from lung images.
3. To analyze acoustic patterns from respiratory audio.
4. To combine CNN-based spectral analysis with Transformer-based temporal analysis for audio.
5. To use ResNet50 for lung image classification.
6. To incorporate Explainable AI techniques to understand model predictions.
7. To classify respiratory conditions into Normal, Pneumonia, and Tuberculosis.

---

##  Proposed Methodology

The proposed framework consists of two major processing pipelines:

```text
                    Input Data
                       │
          ┌────────────┴────────────┐
          │                         │
     Lung Images              Respiratory Audio
          │                         │
          ↓                         ↓
 Image Preprocessing         Audio Preprocessing
          │                         │
          ↓                  ┌──────┴──────┐
       ResNet50              │             │
          │             Mel-Spectrogram   MFCC
          │                  │             │
          │                  ↓             ↓
          │                 CNN      Transformer
          │                  │             │
          │                  └──────┬──────┘
          │                         │
          ↓                         ↓
   Image Prediction          Audio Prediction
          │                         │
          └────────────┬────────────┘
                       ↓
              Disease Classification
                       │
             ┌─────────┴─────────┐
             │         │         │
           Normal  Pneumonia  Tuberculosis
                       │
                       ↓
               Explainable AI
             ┌─────────┴─────────┐
             │                   │
          Grad-CAM       Transformer Attention
```

---

##  Image Processing Pipeline

The image pipeline processes chest-related medical images obtained from the selected datasets.

The preprocessing steps include:

* Image resizing
* Normalization
* Data augmentation

The images are resized to **224 × 224 pixels** before being provided to the model.

A pretrained **ResNet50** architecture is used for visual feature extraction and classification.

ResNet50 was selected because of its residual learning capability and ability to capture visual features relevant to lung abnormalities.

---

## Audio Processing Pipeline

The respiratory audio pipeline consists of preprocessing and two complementary feature-learning branches.

### Audio Preprocessing

The audio data undergoes:

* Noise reduction
* Silence removal
* Feature extraction

Two representations are generated:

### 1. Mel-Spectrogram

Mel-spectrograms are used to represent spatial-frequency patterns in the respiratory audio.

A **CNN** is used to extract spectral features from the Mel-spectrograms.

### 2. MFCC

Mel-Frequency Cepstral Coefficients (MFCCs) are used to represent temporal acoustic characteristics.

A **Transformer** architecture is used to model long-range temporal dependencies in the MFCC sequences.

The outputs from the CNN and Transformer branches provide a comprehensive audio representation.

---

##  Models Used

| Modality             | Model                 | Purpose                                      |
| -------------------- | --------------------- | -------------------------------------------- |
| Lung Images          | ResNet50              | Visual feature extraction and classification |
| Audio                | CNN                   | Mel-spectrogram feature extraction           |
| Audio                | Transformer           | MFCC temporal pattern analysis               |
| Image Explainability | Grad-CAM              | Highlight important image regions            |
| Audio Explainability | Transformer Attention | Identify important audio segments            |

---

## Explainable AI

Explainable AI is incorporated to provide qualitative insight into the model predictions.

### Grad-CAM

**Gradient-weighted Class Activation Mapping (Grad-CAM)** is applied to chest images.

It produces heatmaps highlighting regions of the lung images that contributed to the model's prediction.

These visualizations help identify relevant regions associated with patterns such as:

* Opacities
* Cavitations
* Consolidation regions

### Transformer Attention

Transformer attention is used for the audio branch.

The attention analysis identifies important time segments in respiratory audio that contribute to the classification.

The project reports high-attention segments corresponding to acoustic patterns such as cough bursts and abnormal breath cycles.

---

## Dataset

The datasets used in this project were obtained from **Kaggle**.

The data contains three main classes:

```text
Normal
Pneumonia
Tuberculosis
```

The project uses both:

* Chest/lung imaging data
* Respiratory audio recordings

The data was organized into the three disease classes and divided using an **80:20 stratified train-test split**, with 20% of the training data used for validation.


---

## Results

The evaluated models achieved the following test accuracies:

| Model             | Modality | Test Accuracy |
| ----------------- | -------- | ------------: |
| CNN + Transformer | Audio    |   **88.37%**  |
| ResNet50          | Image    |  **93.57%**   |

The image classification model achieved a test accuracy of **93.57%**, while the audio model achieved **88.37%** on the evaluated three-class classification task.

The results reported in this repository are based on the experiments described in the accompanying research paper.

---

##  Key Findings

The project demonstrates that:

* Lung images can provide useful structural information for respiratory disease classification.
* Respiratory audio can provide complementary acoustic information.
* CNNs can extract spectral patterns from Mel-spectrograms.
* Transformers can model temporal patterns in MFCC sequences.
* ResNet50 can be used for lung image feature extraction and classification.
* Grad-CAM can provide qualitative visual explanations.
* Transformer attention can highlight important audio segments.

The multimodal framework is designed to support analysis using image data, audio data, or both modalities.

---

## Technologies and Concepts

### Deep Learning

* Convolutional Neural Networks (CNN)
* ResNet50
* Transformer Networks
* Transfer Learning

### Audio Processing

* Mel-Spectrogram
* MFCC
* Short-Time Fourier Transform (STFT)
* Noise Reduction
* Silence Removal

### Image Processing

* Image Resizing
* Normalization
* Data Augmentation

### Explainable AI

* Grad-CAM
* Transformer Attention

### Application Area

* Medical Imaging
* Respiratory Audio Analysis
* Multimodal Artificial Intelligence
* Respiratory Disease Classification

---
##Future Work

Future work will focus on:

* Increasing the dataset size
* Including additional respiratory diseases
* Improving the multimodal integration of audio and image information
* Further validating the framework using larger and more diverse datasets
* Improving the clinical applicability of the system

## ⭐ Project Summary

**Multimodal Deep Learning System for Detecting Respiratory Diseases Using Lung Imaging and Respiratory Audio**

> A multimodal AI framework combining **ResNet50-based lung image analysis** with **CNN + Transformer-based respiratory audio analysis** for classification of **Normal, Pneumonia, and Tuberculosis**, with **Grad-CAM and Transformer attention** for explainability.
