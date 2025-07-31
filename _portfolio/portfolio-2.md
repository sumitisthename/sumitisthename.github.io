---
title: "Real-Time Attendance System using Face Recognition"
excerpt: "<img src='/images/face-recognition.png'>"
collection: portfolio
date: 2023-12-01
tags: [Computer Vision, Deep Learning, Face Recognition, OpenCV, SVM, Python]
categories: [AI/ML, Computer Vision]
header:
  image: /images/face-recognition.png
  teaser: /images/face-recognition.png
  caption: "Automated attendance system using facial recognition"
---

## 🎯 Problem Statement

Traditional attendance systems are manual, error-prone, and inefficient. In large-scale environments, this leads to inaccurate records and administrative overhead. This project solves that by implementing an **automated real-time facial recognition system** for attendance tracking.

## 🏗️ System Architecture

| Component           | Technology               | Purpose                                 |
|---------------------|--------------------------|-----------------------------------------|
| Face Detection      | OpenCV DNN (SSD)         | Localize faces in real-time             |
| Feature Extraction  | FaceNet                  | Generate 128D facial embeddings         |
| Classification      | Support Vector Machine   | Match embeddings to known identities    |
| Image Preprocessing | OpenCV                   | Standardize and normalize inputs        |
| Development         | Python                   | Backend logic and ML integration        |

## 🔄 Working Methodology

### 1. Image Preprocessing
- Resize to 160x160 pixels
- Normalize color channels
- Create blob for DNN model input

```python
def preprocess_image(image):
    image = cv2.resize(image, (160, 160))
    blob = cv2.dnn.blobFromImage(
        image, scalefactor=1.0,
        size=(160, 160), mean=(127.5, 127.5, 127.5),
        swapRB=True
    )
    return blob
