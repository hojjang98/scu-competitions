# 🍽️ Food Image Classification

> *"I heard computer vision is trending these days..."*

This project started with that simple thought.  
While studying machine learning, I learned from my professor that the field of computer vision (CV) is rapidly gaining momentum and practical importance.  
Curious and excited, I decided to jump into it and explore image classification through this beginner-friendly project.

## 🎯 Project Goal

- Build a food image classifier using CNN and transfer learning.
- Gain hands-on experience with core CV tasks: preprocessing, augmentation, and evaluation.
- Understand the fundamentals of image classification in a practical, applied context.

## 📁 Dataset

- **Source**: [Fruits and Vegetables Image Recognition DataSet](https://www.kaggle.com/datasets/kritikseth/fruit-and-vegetable-image-recognition)
- **Size**: 101 food categories, 101,000 images  
  *(Note: I will use a smaller subset for faster experimentation.)*

## 🔧 Techniques Used

- Convolutional Neural Networks (CNN)
- Transfer Learning (ResNet, EfficientNet)
- Image Augmentation (`ImageDataGenerator`)
- Evaluation: Accuracy, Confusion Matrix, Visual Predictions

## 🧱 Project Structure

food-image-classification/
├── data/
│   ├── raw/                  # Original downloaded dataset
│   └── processed/            # Resized / cleaned / sampled images
│
├── notebooks/
│   ├── 01_eda.ipynb          # EDA & class distribution, sample visuals
│   └── 02_modeling.ipynb     # CNN / transfer learning, training + evaluation
│
├── models/                   # Saved model weights (.h5 or .pt)
│
├── figures/                  # Plots, confusion matrix, prediction samples
│
├── utils/                    # (optional) helper functions like image loading, evaluation
│   └── data_loader.py
│
├── README.md
└── requirements.txt
