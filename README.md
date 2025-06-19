
# Refining CAPTCHA using Machine Learning model 

A machine learning-based solution to refine and decode CAPTCHA images using deep learning techniques.

### Project Description:
This project develops a system that automatically solves CAPTCHA images using a combination of Convolutional Neural Networks (CNNs) and Bidirectional Long Short-Term Memory (BiLSTM) models. The system is trained on synthetically generated CAPTCHA images and evaluated on unseen examples. The end goal is to improve CAPTCHA recognition accuracy through deep learning-based OCR (Optical Character Recognition).

## Contents:

* Project Overview
* Dataset Generation
* Data Preprocessing
* Model Architecture

  * Baseline CNN
  * Primary CLSTM Model
* OCR Role
* Why CNN and BiLSTM?
* Results & Observations
* Conclusion

##  Project Overview
CAPTCHAs are widely used for distinguishing humans from bots, often containing distorted characters. This project builds a deep learning pipeline to solve such CAPTCHA images automatically. It involves generating synthetic datasets, preprocessing images, training multiple models, and comparing accuracy results.

##  Dataset Generation

* Random alphanumeric strings are generated using Python.
* CAPTCHA images are created using PIL with added noise and distortion (lines, dots).
* Images are saved with filenames representing the ground-truth text.
* User can specify the number of images for training, validation, and testing.


##  Data Preprocessing

* Convert image to grayscale.
* Apply median filtering to reduce noise.
* Invert the image to improve contrast between characters and background.

These steps simplify the image content and enhance model performance.

##  Model Architecture

### Baseline Model – CNNCharNet

* Uses a Convolutional Neural Network to extract features.
* CAPTCHA is split into 5 parts, each processed individually.
* Character-level classification.
* Acts as a reference to evaluate performance of the advanced model.

### Primary Model – CLSTM (CNN + BiLSTM + CTC Loss)

* CNN layers extract spatial features from the full CAPTCHA image.
* BiLSTM layers learn the sequential relationship between characters.
* Connectionist Temporal Classification (CTC) Loss is used for training.
* Decoder functions convert prediction outputs into readable text.

##  OCR Role in CAPTCHA Solving

* OCR techniques are integrated with deep learning to convert image-based CAPTCHA into text.
* Preprocessing (grayscale, noise removal, inversion) improves OCR effectiveness.
* OCR output is compared with ground-truth text for accuracy calculation.

## ℹ️More Information:
 
 ### Why CNN?

* To Extract visual features(edges, corners, curves).
* Invariant to image shifts, scales, and distortions.
* Efficient for pattern recognition in character shapes.

### Why BiLSTM?

* Understands sequential nature of CAPTCHA strings.
* Reads input both forward and backward.
* Handles overlapping or variably spaced characters.
* Provides context-aware predictions.

### 📈 Results & Observations
![28X28 MATRIX](https://github.com/user-attachments/assets/a9b47351-bd0e-483b-a365-6441092b3511) 

This image is a 28×28 matrix of random values visualized as an image, often used to test preprocessing or model input pipelines. It’s not meaningful in terms of content



* CNN-only model performed decently but lacked sequence understanding.
* CLSTM model achieved up to 52.6% full-sequence accuracy.

  Accuracy Graphs:

   ![download2](https://github.com/user-attachments/assets/1b3edea7-9032-4a43-aa65-ab0cb1b678b8)
    ![download](https://github.com/user-attachments/assets/d1ef5dbb-29d2-48fd-9019-485286aa0699)

* Confusions observed between visually similar characters like ‘O’ and ‘0’, or ‘8’ and ‘g’.
* Model struggled with extreme distortions and high-noise images.

### Data Structure Verification:


![Data structure verification](https://github.com/user-attachments/assets/e267253e-6c0d-4ae8-ae16-2e04e45dcc06)

Why do we use this specifically?

To verify image data shape

 → Are the images of shape [batch_size, 1, 28, 28]? (for grayscale)

To inspect labels

 → Are the labels aligned correctly?


 
 → Do they contain 5 integers per image (indicating 5 characters)?

Debugging
 

 
 → Check if preprocessing worked (e.g., normalization, resizing)


 
 → Confirm whether images and labels are paired correctly
 
 
 
 → Useful before training or evaluating your model




