# Driver Drowsiness Detection System

# Overview
The Driver Drowsiness Detection System is a Python-based project that uses computer vision and deep learning to detect drowsiness in drivers. By analyzing the state of the eyes (open or closed) through a webcam feed, it can alert drivers if they are at risk of falling asleep while driving.

# Model


# 1. Input Data Preprocessing
Grayscale Conversion: Images are converted to grayscale to simplify computations since color information is not essential for detecting eye states.
Rescaling: All pixel values are rescaled to the range [0, 1] (using rescale=1./255) to normalize the data and improve model performance.
Target Size: Images are resized to (24, 24) for uniformity and to reduce computational load.

#2. Model Architecture
# Convolutional Layers
 - Conv2D (32 filters, 3x3 kernel):
 - The first layer extracts low-level features like edges and textures.
 - Uses ReLU activation to introduce non-linearity.
Conv2D (64 filters, 3x3 kernel):
- Deeper layers learn more complex features (e.g., patterns specific to closed or open eyes).
 - Pooling Layers
MaxPooling2D:
 - Reduces the spatial dimensions of feature maps.
 - Keeps the most important features, helping to make the model invariant to small translations of input data.
3. Regularization

# Dropout Layers:
Dropout(0.25) after convolutional layers:
 - Randomly sets 25% of neurons to zero during training to reduce overfitting.
 - Dropout(0.5) after the fully connected layer:
 - Prevents overfitting by ensuring robust learning in the final dense layers.

# 4. Dense Layers
Flatten:
 - Converts the multidimensional feature maps into a 1D vector.
Dense(128, activation='relu'):
 - Fully connected layer with 128 neurons for high-level feature integration.
Dense(2, activation='softmax'):
 - Final output layer with 2 neurons (for Open and Closed classes).
Uses softmax activation to output class probabilities.

# 5. Model Compilation
Optimizer: Adam:
 - Combines the benefits of Adaptive Gradient Algorithm (AdaGrad) and Root Mean Square Propagation (RMSProp).
 - Efficient and robust for handling sparse gradients.
Loss Function: categorical_crossentropy:
 - Suitable for multi-class classification tasks.
Metrics: accuracy:
 - Tracks model performance during training and validation.

# 6. Training
Batch Size: 32:
 - A balanced batch size for training on typical hardware while ensuring reasonable convergence speed.
Epochs: 15:
 - Sufficient for this simple architecture and dataset size.
Steps Per Epoch: Calculated based on the dataset size divided by the batch size.

# 7. Output
The model is saved as cnnCat2.h5 in the models/ directory for use in real-time detection.

# Setup Instructions
1. Pre-Trained Model
Ensure the cnnCat2.h5 model is in the models/ directory. If unavailable, you can train a new model using the model.py script (see "Training the Model").

2. Haar Cascades
Ensure the Haar Cascade files (haarcascade_frontalface_alt.xml, haarcascade_lefteye_2splits.xml, haarcascade_righteye_2splits.xml) are in the haar cascade files/ directory. These files are used to detect facial features.

3. Alarm
The alarm.wav file is the sound played when drowsiness is detected. You can replace it with a custom .wav file.

# Features
1. Real-Time Eye Detection: Detects whether the driver's eyes are open or closed using Haar Cascades.
2. Drowsiness Detection: Uses a CNN model to classify the state of the eyes.
3. Alarm System: Triggers an alarm when the eyes remain closed for a prolonged period.
4. Scoring Mechanism: Maintains a score to track drowsiness levels, incrementing for closed eyes and resetting for open eyes.
