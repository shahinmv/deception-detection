# Audio-Based Deception Detection

This repository contains the implementation of a machine learning pipeline to predict whether a story from audio files is true or deceptive. The pipeline consists of multiple stages: preprocessing, transformation, model training, and ensemble prediction.

## Table of Contents
1. [Overview](#overview)
2. [Pipeline Stages](#pipeline-stages)
   - [Preprocessing Stage](#41-preprocessing-stage)
   - [Transformation Stage](#42-transformation-stage)
   - [Model Stage](#43-model-stage)
   - [Ensemble Stage](#44-ensemble-stage)
3. [Usage](#usage)
4. [Dependencies](#dependencies)
5. [Contributing](#contributing)
6. [License](#license)

---

## Overview

The goal of this project is to build a robust ML model that can analyze audio files and classify them as either true or deceptive. The repository includes scripts, data preprocessing routines, feature extraction techniques, and machine learning models.

---

## Pipeline Stages

### 4.1 Preprocessing Stage

The preprocessing stage ensures that the raw audio files are consistent and ready for feature extraction.

- **Input**: Raw audio files (`.wav`).
- **Steps**:
  1. **Clean Audio**:
     - Normalize the amplitude of the audio.
     - Remove silence.
  2. **Audio Augmentation**:
     - Apply pitching, time-stretching, and inject noise to augment data.
  3. **Padding/Truncation**:
     - Shorten all audio clips to 30 seconds.
- **Output**: Cleaned and standardized audio data.

---

### 4.2 Transformation Stage

The transformation stage converts cleaned audio data into numerical features suitable for machine learning.

- **Input**: Cleaned audio data.
- **Steps**:
  1. **Feature Extraction**:
     - **Temporal Features**: Zero crossing rate, RMS energy.
     - **Spectral Features**: MFCCs, chroma, spectral centroid, bandwidth, contrast, flatness, rolloff.
     - **Rhythmic Features**: Tempo.
     - **Harmonic/Percussive Components**: Tonal and percussive decomposition.
     - **Mel Spectrogram**: Time-frequency representation.
  2. **Feature Scaling**:
     - Normalize and standardize features for consistency.
  3. **Feature Selection**:
     - Identify the most relevant features using techniques like Random Forest or XGBoost.
- **Output**: Feature vectors in tabular format.

---

### 4.3 Model Stage

The model stage trains a learning algorithm on the extracted features.

- **Input**: Feature vectors.
- **Steps**:
  1. **Model Selection**:
     - Gradient Boosting (XGBoost, LightGBM).
     - Random Forests.
     - Support Vector Machines.
     - Logistic Regression.
  2. **Hyperparameter Tuning**:
     - Optimize hyperparameters using grid search or random search.
  3. **Training**:
     - Train models on the training set.
     - Evaluate model performance using metrics:
       - Accuracy
       - Precision
       - Recall
       - F1-Score
       - Confusion Matrix
- **Output**: Predicted probabilities.

---

### 4.4 Ensemble Stage

The ensemble stage combines predictions from multiple models to improve overall accuracy and robustness.

- **Input**: Predictions from multiple models.
- **Steps**:
  1. **Voting Mechanism**:
     - Use soft or hard voting to aggregate predictions.
  2. **Weight Assignment**:
     - Assign weights to models based on their validation performance.
  3. **Final Prediction**:
     - Combine individual predictions to produce a single output.
- **Output**: Final ensemble prediction.

---

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/shahinmv/audio-deception-detection.git
