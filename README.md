# Audio-DeepFake-Classification

### Project Description
This project focuses on detecting audio deepfakes by developing a deep learning model that differentiates between genuine (real) and manipulated (spoof) audio recordings. The goal is to identify artificially altered speech designed to imitate authentic voices. The model is trained and evaluated using the ASVspoof 2017 dataset(provided in the dataset repo of the project assessment).

### Project Overview

- **Dataset:** ASVspoof 2017 dataset containing genuine and spoof audio recordings.
- **Preprocessing:** Convert audio to log-scaled Mel spectrograms, resize, normalize, and augment (noise, pitch shift, time stretch) for better training.
- **Data Splitting:** Train-validation split for model generalization.
- **Model Architecture:** Hybrid EfficientNet with CNN layers for feature extraction.
- **Training:** Binary classification with Adam optimizer and binary cross-entropy loss.
- **Real-Time Detection:** Implement real-time audio inference for AI vs. human speech.
- **Evaluation:** Test model on unseen data and analyze performance metrics.


