# Digit Classifier (CNN)

This project implements a Convolutional Neural Network (CNN) using Keras to recognize and classify handwritten digits (0-9) from the famous **MNIST dataset**.

## Overview

The model takes grayscale images of handwritten digits (28x28 pixels) and outputs a probability distribution across the 10 possible digit classes. The architecture includes multiple convolutional layers to extract spatial features, batch normalization to stabilize and speed up training, and dropout layers to prevent overfitting.

## Features
- **Dataset:** MNIST (60,000 training images, 10,000 test images).
- **Architecture:** Convolutional Neural Network (CNN) built with `Sequential` API.
- **Optimization:** `Adam` optimizer for efficient gradient descent.
- **Loss Function:** `categorical_crossentropy` (standard for multi-class classification).
- **Regularization:** `BatchNormalization` and `Dropout` (20%).

## Requirements

To run this project, ensure you have Python installed along with the following libraries:

```bash
pip install tensorflow matplotlib numpy
```

## Model Architecture

1. **Input Layer:** Accepts `28x28x1` arrays (grayscale images).
2. **Convolutional Block 1:** 
   - `Conv2D` with 32 filters (3x3 kernel), ReLU activation.
   - `BatchNormalization`.
   - `MaxPooling2D` (2x2 pool size).
3. **Convolutional Block 2:** 
   - `Conv2D` with 32 filters (3x3 kernel), ReLU activation.
   - `BatchNormalization`.
   - `MaxPooling2D` (2x2 pool size).
4. **Flatten Layer:** Converts the 2D feature maps into a 1D vector.
5. **Dense Block:** 
   - Fully connected layer with 128 units, ReLU activation.
   - `Dropout` (0.2).
   - Fully connected layer with 128 units, ReLU activation.
   - `Dropout` (0.2).
6. **Output Layer:** Dense layer with 10 units and `softmax` activation (outputs probabilities for digits 0-9).

## Usage

1. **Load and Preprocess Data:** The script automatically downloads the MNIST dataset, reshapes the images to include the channel dimension, normalizes the pixel values to the range `[0, 1]`, and one-hot encodes the labels.
2. **Train the Model:** The model is trained using a batch size of 128 for 5 epochs. 
3. **Evaluate:** After training, the script evaluates the model against the 10,000 unseen test images.

## Expected Results

After training for just 5 epochs, the model typically achieves an accuracy of **over 98.5%** on the validation/test dataset.
