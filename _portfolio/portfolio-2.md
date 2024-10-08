---
title: "Real Time Attendance System using Face Recognition"
excerpt: "<img src='/images/face-recognition.png'>"
collection: portfolio
---

## Problem Statement
Student’s attendances are taken manually using attendance sheets which is a time consuming event. Moreover, in a large classroom it is difficult to find out if the claimed student is actually present or not. Since it is difficult to overcome the above two mentioned problems by manual labour this project depicts an automated attendance system using face recognition to tackle the same.


![Face_Recognition](/images/portfolio2-block-diagram.png)

### Working Methodology

The face recognition attendance system follows a streamlined process for identifying and verifying individuals. Here's a concise overview of the methodology:

1. **Resizing**:
   - The input image is resized to a fixed dimension to maintain consistency.

2. **Blob Creation**:
   - A binary large object (BLOB) is created from the resized image, which is then used for further processing.

3. **Face Detection**:
   - The system detects faces in the image using pre-trained models. The detected faces are highlighted with bounding boxes.

4. **Blob Extraction**:
   - For each detected face, another BLOB is created to focus on the specific face region.

5. **Embedding Generation**:
   - The face BLOB is converted into an embedding, a numerical representation that captures the unique features of the face.

6. **SVM Classification**:
   - The face embeddings are fed into a Support Vector Machine (SVM) classifier, which identifies and verifies the individual's identity based on the stored embeddings.

![Working](/images/working-methodology.png)

## Image Preprocessing 

We preprocess the image for better performance of the Deep Learning network. This helps in combating illumination changes. This function performs two main operations:

1. **Mean Subtraction**
2. **Scaling**

The preprocessing is done using the following OpenCV function:

```python
imageBlob = cv2.dnn.blobFromImage(image, scalefactor=1.0, size, mean, swapRB)
```

## Face Detection Using Deep Learning

We are using Deep Learning face detectors available in OpenCV for face detection. OpenCV’s DL face detector is based on SSD (Single Shot MultiBox Detector) with a ResNet base network. We chose this approach over Haar cascades because it performs well in a wide variety of scenarios, including:

- **Face with Tilt**: The DL face detector can accurately detect faces even when they are tilted.
- **Low Light Conditions**: The detector is effective in relatively dark environments.
- **.prototxt file**: Contains the architecture of the network.
- **.caffeemodel**: Contains the weights of the network.

![Face_Detection](/images/face-detect.png)

### SSD

- Single Shot : This means that the tasks of object localization and classification are done in single forward pass of network.
- This builds up on the VGG-16 but discards the fully connected layers. This is because VGG-16 has strong performance in high quality image classification

### FaceNet
FaceNet is used to convert the image into embeddings (128D)

![Embeddings](/images/Embeddings.png)

## Face Recognition Process

- **Face recognition** is a one-to-many check of the probe image with all images in the dataset.
- The process is completed by computing a similarity index between images.
- This uniquely identifies the probe image.

![FaceMatch](/images/face-match.png)

## Results

| Training Images | Testing Images | Accuracy (%) |
|-----------------|----------------|--------------|
| 1500            | 1500           | 95%          |
| 1800            | 1200           | 96.21%       |
| 2100            | 900            | 97.31%       |
