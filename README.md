# Audio-DeepFake-Classification

### Project Description
This project focuses on detecting audio deepfakes by developing a deep learning model that differentiates between genuine (real) and manipulated (spoof) audio recordings. The goal is to identify artificially altered speech designed to imitate authentic voices. The model is trained and evaluated using the ASVspoof 2017 dataset(provided in the dataset repo of the project assessment).

### Project Overview
- **Dataset:** ASVspoof 2017 dataset containing genuine and spoofed audio recordings.
- **Preprocessing:** Convert audio to log-scaled Mel spectrograms, pad/truncate to a fixed length, and normalize for better training.
- **Data Splitting:** Train-validation split (80-20) with stratification to maintain class balance.
- **Model Architecture:** Simplified EfficientNetB0-based model with a Global Average Pooling layer and fully connected layers for classification.
- **Training:** Binary classification using the Adam optimizer and binary cross-entropy loss, with formatted epoch logs for better monitoring.
- **Inference:** Supports batch predictions for detecting AI-generated speech in new audio files.
- **Evaluation:** Test model performance using accuracy and loss metrics on unseen validation data.

### Dataset Details
This project uses the ASVspoof 2017 dataset, which contains genuine and spoofed audio recordings.
- **Link:** https://datashare.ed.ac.uk/handle/10283/3055

### Selection
Use case:
- Detecting AI-generated human speech
- Potential for real-time or near real-time detection
- Analysis of real conversations
Three models that show the most promise for our testcase would be
  1. EfficientNetB0 model
  2. ResNet18 or VGG
  3. RawNet2 with Sinc Filters

`Later concluded that EfficientNet would be suitable as it contains more hidden layers, also shows good performance on spectrogram-like data as it can capture both local time-frequency patterns and global temporal cues.`
