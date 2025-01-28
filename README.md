# Driver Drowsiness Detection System

# Overview
The Driver Drowsiness Detection System is a Python-based project that uses computer vision and deep learning to detect drowsiness in drivers. By analyzing the state of the eyes (open or closed) through a webcam feed, it can alert drivers if they are at risk of falling asleep while driving.

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
