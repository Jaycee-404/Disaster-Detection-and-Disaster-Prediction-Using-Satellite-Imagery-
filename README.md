# Disaster-Detection-and-Disaster-Prediction-Using-Satellite-Imagery

![MIT License](https://img.shields.io/badge/License-MIT-green.svg)

## Objective
The objective of this project is to detect and predict disaster-affected areas in satellite or aerial images using deep learning. The system integrates anomaly detection through reconstruction loss and binary classification via a ResNet50-based model to identify damage patterns in pre- and post-disaster scenarios.

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

### Disaster Prediction (Supervised)
- A labeled dataset is created by pairing pre-disaster images with labels extracted from corresponding post-disaster annotations.
- A convolutional neural network based on ResNet50 is used for binary classification.
- The model is trained to predict whether a pre-disaster image corresponds to a post-disaster scene with damage.

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

- **Integrated Pipeline**:
  - Combined both unsupervised anomaly detection and supervised classification into a unified end-to-end disaster monitoring solution.
  - Enables real-time, automated alerts and improves situational awareness in disaster response systems.


## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/Jaycee-404/Disaster-Detection-and-Disaster-Prediction-Using-Satellite-Imagery-/tree/main?tab=MIT-1-ov-file) file for details.
