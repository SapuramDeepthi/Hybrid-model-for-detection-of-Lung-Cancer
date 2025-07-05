# Lung CT Image Classification and Segmentation Project

## 🩺 Project Overview
This project focuses on classifying and segmenting lung CT scan images into four classes:
- Normal
- Adenocarcinoma
- Squamous Cell Carcinoma
- Large Cell Carcinoma

It combines traditional image processing techniques with deep learning models to build an effective diagnostic pipeline.


## 📁 Dataset
- Source: Google Drive (mounted in Google Colab)
- Format: .zip file containing folders of images for each class
- Structure after extraction**:
  lungct/
  ├── adenocarcinoma/
  ├── squamouscell/
  ├── largecell/
  └── normal/

## 🔧 Preprocessing Steps

### 1. Image Loading and Normalization
- Images are resized to 256x256
- Grayscale images are normalized to range [0, 1]

### 2. Noise Removal
- Median filtering is applied to reduce salt-and-pepper noise

### 3. Thresholding
- Otsu's method is used to binarize images based on intensity

### 4. Morphological Processing
- Morphological opening operation is applied to clean the segmented masks

### 5. Active Contour (Snakes)
- Applied for contour-based segmentation of lung regions

### 6. Circle Hough Transform (CHT)
- Detects circular shapes (possible tumors) to extract features

## 🤖 Deep Learning Models

### 📌 CNN Classifier
- Input: 128x128 grayscale images
- Layers:
  - Conv2D + MaxPooling
  - Flatten + Dense + Dropout
- Output: 4-class softmax
- Evaluation: Accuracy, Precision, Recall, F1-score
- Model saved as: `lung_cancer_model.h5`

### 📌 Transfer Learning with VGG19 (HOVG-Net)
- Uses pretrained VGG19 from Keras Applications
- Input: Grayscale images converted to 3-channel format
- VGG19 is frozen (non-trainable)
- Custom classifier layers on top
- Model saved as: `hovg_net_model.h5`

---

## 📊 Evaluation Metrics
- Accuracy
- Precision (weighted)
- Recall (weighted)
- F1-Score(weighted)

---

## 💾 Model Saving
- Final models are saved to Google Drive for future use:
  
  /content/drive/MyDrive/lung_cancer_model.h5
  /content/hovg_net_model.h5

## 🧰 Tools and Libraries
- Python 3
- OpenCV
- NumPy, Matplotlib
- scikit-image
- TensorFlow & Keras
- scikit-learn
- Google Colab

## 📎 How to Run
1. Upload dataset zip to Google Drive
2. Mount drive in Colab
3. Run preprocessing cells
4. Train the CNN and VGG19 models
5. Evaluate and save models


## 📬 Acknowledgements
- Medical image datasets from public repositories
- Keras and TensorFlow documentation
- OpenCV and scikit-image for image processing


## 📷 Sample Output
- Median filtered image
- Binary mask (Otsu threshold)
- Active contour overlay
- Circle Hough Transform detection

