# Bio-adaptive closed-loop system for detection of Cardiac Arrhythmias

This repository contains three progressively advanced implementations of a clinical music therapy system integrating EEG signal analysis and AI-generated music. The system aims to generate personalized therapeutic music using physiological data (EEG, GSR, HRV) and deep learning models.

---

## Table of Contents

- [Motivation](#motivation)  
- [Background](#background)  
- [Goals](#goals)  
- [Overview](#overview)  
- [Implementation Versions](#implementation-versions)  
  - [Version 1: Basic EEG Predictor + Feedback Loop](#version-1-basic-eeg-predictor--feedback-loop)  
  - [Version 2: CNN-LSTM EEG Predictor + MusicGen Adapter](#version-2-cnn-lstm-eeg-predictor--musicgen-adapter)  
  - [Version 3: EEG Dataset Training + Music Generation + Session Logging](#version-3-eeg-dataset-training--music-generation--session-logging)  
- [Setup and Dependencies](#setup-and-dependencies)  
- [Usage](#usage)  
- [Contributing](#contributing)  
- [License](#license)  

---

## Motivation

Music therapy has demonstrated profound benefits in managing mental health, reducing stress, and improving emotional wellbeing. However, personalizing therapy to a patient's current physiological and emotional state remains challenging. This project seeks to bridge that gap by combining real-time brainwave analysis with AI music generation, creating adaptive, data-driven therapeutic music tailored to individual needs.

---

## Background

Electroencephalography (EEG) measures electrical brain activity, providing insight into cognitive and emotional states through brainwave patterns such as alpha, beta, and gamma rhythms. Physiological signals like galvanic skin response (GSR) and heart rate variability (HRV) further enrich emotional state understanding.

Recent advances in deep learning enable automatic extraction of meaningful features from EEG data. Meanwhile, generative AI models like Facebook’s MusicGen can create high-quality music conditioned on textual descriptions. By integrating these technologies, it is possible to design a closed-loop system that dynamically modulates therapeutic music based on a patient's biofeedback.

---

## Goals

- Develop EEG-based deep learning models to predict emotional states from physiological signals.  
- Use physiological data (GSR, HRV) to inform music generation parameters such as tempo and brightness.  
- Generate personalized therapeutic music with AI that adapts to patient feedback in near real-time.  
- Provide logging and visualization tools for clinicians to monitor therapy progression.  
- Build modular versions that progressively add complexity, from basic CNN models to dataset training and session management.  

---

## Overview

Clinical music therapy systems leverage physiological signals to tailor music therapy in real-time. This project combines:

- EEG-based deep learning models predicting emotional states or valence from brain signals.  
- AI music generation models (Facebook's MusicGen) to create personalized therapeutic audio.  
- Physiological feedback loops incorporating GSR (galvanic skin response) and HRV (heart rate variability).  
- Logging and visualization for therapy sessions.

---

## Implementation Versions

### Version 1: Basic EEG Predictor + Feedback Loop

- Simple CNN-based EEG predictor outputs 5 EEG band probabilities from audio input.  
- Physiological feedback loop uses GSR and HRV data to adjust music parameters (tempo, brightness, complexity).  
- Generates 30-second music with MusicGen based on adjusted descriptors.  
- Example output:
    Generated music with adjustments: {'tempo': 88, 'brightness': 0.2, 'complexity': 0.9}
**Code highlights:**  
- Uses torchaudio’s MelSpectrogram and Conv2d layers.  
- Sigmoid outputs for EEG bands (delta, theta, alpha, beta, gamma).  
- Simple music descriptors adapted from physiological factors.

---

### Version 2: CNN-LSTM EEG Predictor + MusicGen Adapter

- Upgraded EEG predictor with CNN followed by LSTM to capture temporal dependencies.  
- MusicGen Adapter class wraps the music generation model with custom duration and description.  
- Improved physiological feedback loop producing descriptive text for mood-based music generation.  
- Session logging outputs JSON with biofeedback and descriptors.

**Example output:**  Music generated and logged: Relaxing piano, 90 BPM, brightness 0.20, complex structure

**Code highlights:**  
- LSTM layer enhances EEG temporal modeling.  
- Generates human-readable descriptors like "Relaxing piano, 90 BPM".  
- JSON session logging with timestamps.  

---

### Version 3: EEG Dataset Training + Music Generation + Session Logging

- Full pipeline from dataset loading, model training, to therapy session management.  
- Loads and preprocesses GameEmo EEG dataset with channel selection and trial padding.  
- 1D-CNN EEG regression model trained on valence scores from SAM ratings.  
- ClinicalMusicTherapySystem class integrates trained EEG model and MusicGen for music generation.  
- Session logging to JSON file and valence trend plotting with matplotlib.  
- Supports GPU acceleration if available.

**Code highlights:**  
- Dataset class handles multiple subjects and trial standardization.  
- Uses `kagglehub` to download the EEG dataset automatically.  
- Detailed logging with timestamps for long-term therapy session analysis.  

---

## Setup and Dependencies

1. Clone the repository:
   ```bash
   git clone https://github.com/dreamboat26/Bio-adaptive-closed-loop-system-for-detection-of-Cardiac-Arrhythmias.git
   cd Bio-adaptive-closed-loop-system-for-detection-of-Cardiac-Arrhythmias

## Usage 
Run the .ipynb notebook

## Contributing
This was made in relation to short term project effort under supervison of Prof. Nicholas Peters 

## License

This project is licensed under the MIT License.
