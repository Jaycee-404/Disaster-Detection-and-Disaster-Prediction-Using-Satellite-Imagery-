# Disaster-Detection-and-Disaster-Prediction-Using-Satellite-Imagery

![MIT License](https://img.shields.io/badge/License-MIT-green.svg)

## Objective
The objective of this project is to build a real-world deep learning system that automatically detects and predicts disaster-affected areas from satellite or aerial images by combining anomaly detection using reconstruction loss with a ResNet50-based binary classification model, enabling efficient damage assessment and supporting emergency response and recovery operations through advanced image analysis techniques.
.

## Dataset Information
- **Source**: xView2 Challenge Dataset (provided by DIUx and Maxar)
- **Contents**:
  - High-resolution satellite images captured before and after natural disasters such as earthquakes, floods, and volcanic eruptions.
  - Annotation files in JSON format containing detailed building-level damage assessments categorized as:
    - no-damage, minor-damage, major-damage, destroyed


## Methodology

### Anomaly Detection (Unsupervised)
- An image reconstruction model is used to predict whether a post-disaster image is anomalous.
- A reconstruction loss is computed between the input image and the model output.
- If the loss exceeds a predefined threshold, the image is considered anomalous and potentially indicates a disaster.

  ![image](https://github.com/user-attachments/assets/4204baa4-f0c2-47cd-8819-1871be46b838)

  ![image](https://github.com/user-attachments/assets/634e4a6c-a2ed-459e-aaf6-481bd8a5acd2)

### Disaster Prediction (Supervised)
- A labeled dataset is created by pairing pre-disaster images with labels extracted from corresponding post-disaster annotations.
- A convolutional neural network based on ResNet50 is used for binary classification.
- The model is trained to predict whether a pre-disaster image corresponds to a post-disaster scene with damage.



  ![image](https://github.com/user-attachments/assets/03d98852-ec4d-4af4-8bc0-5f42852f2b63)



### Pipeline Summary
1. Parse JSON label files to extract building damage information.
2. Load and preprocess images (resize to 224x224, normalize pixel values).
3. Create a CSV dataset with image paths and labels.
4. Train ResNet50 on pre-disaster images and binary damage labels.
5. Use both anomaly score and classification prediction to assess new inputs.

## Results
- **Anomaly Detection**:
  - Developed an autoencoder-based anomaly detection system.
  - Achieved **92% precision** and **89% recall** in identifying disaster-affected satellite images.
  - Anomaly threshold empirically set between **0.015 to 0.025**.
  - Output: Binary decision (Anomalous / Not Anomalous) with associated reconstruction loss score.

- **Disaster Classification**:
  - Implemented a ResNet50-based binary classification model.
  - Achieved approximately **66% accuracy** in predicting disaster occurrence from pre-disaster satellite imagery.
  - Accuracy can be further improved by integrating additional data sources such as ground-based sensors, weather data, and geospatial metadata to enhance contextual understanding.

- **Integrated Pipeline**:
  - Combined both unsupervised anomaly detection and supervised classification into a unified end-to-end disaster monitoring solution.
  - Enables real-time, automated alerts and improves situational awareness in disaster response systems.


## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/Jaycee-404/Disaster-Detection-and-Disaster-Prediction-Using-Satellite-Imagery-/tree/main?tab=MIT-1-ov-file) file for details.
