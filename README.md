# Audio-DeepFake-Classification

### Project Description
This project focuses on detecting audio deepfakes by developing a deep learning model that differentiates between genuine (real) and manipulated (spoof) audio recordings. The goal is to identify artificially altered speech designed to imitate authentic voices. The model is trained and evaluated using the ASVspoof 2017 dataset(provided in the dataset repo of the project assessment).

### Dataset Details
This project uses the ASVspoof 2017 dataset, which contains genuine and spoofed audio recordings.
- **Link:** https://datashare.ed.ac.uk/handle/10283/3055

### Project Overview
- **Dataset:** ASVspoof 2017 dataset containing genuine and spoofed audio recordings.
- **Preprocessing:** Convert audio to log-scaled Mel spectrograms, pad/truncate to a fixed length, and normalize for better training.
- **Data Splitting:** Train-validation split (80-20) with stratification to maintain class balance.
- **Model Architecture:** Simplified EfficientNetB0-based model with a Global Average Pooling layer and fully connected layers for classification.
- **Training:** Binary classification using the Adam optimizer and binary cross-entropy loss, with formatted epoch logs for better monitoring.
- **Inference:** Supports batch predictions for detecting AI-generated speech in new audio files.
- **Evaluation:** Test model performance using accuracy and loss metrics on unseen validation data.

### Challenges Encountered
1. Large Dataset:
 `The dataset is too large, making preprocessing will take a considerable amount of time.`
2. Imbalanced Dataset
 `Real and spoofed audio samples were not evenly distributed in the training set, which could bias the model.`

### How These Challenges Were Addressed
1. Large Dataset:
 `I worked on the project using Kaggle to utilize GPU support, which saved me time and made preprocessing quicker.`
2. Imbalanced Dataset:
 `Used Data Augmentation: Applied random time-stretching and pitch-shifting to balance classes and improve generalization.`

###  Assumptions Made:
1. All audio files in the dataset are correctly labeled as "spoof" or "bonafide" according to the protocol file.
2. The training data from the dataset is not discrete, so I used evaluation data for training the model because it contains more than 13000 data points, but most importantly, it is discrete.
3. The ASVspoof 2017 dataset is representative of general spoofing attacks and real speech patterns.

### Selection
Use case:
- Detecting AI-generated human speech
- Potential for real-time or near real-time detection
- Analysis of real conversations
Three models that show the most promise for our testcase would be
  1. EfficientNetB0 model
  2. ResNet18 or VGG
  3. RawNet2 with Sinc Filters

`Later concluded that EfficientNetB0 would be suitable as it contains more hidden layers, also shows good performance on spectrogram-like data as it can capture both local time-frequency patterns and global temporal cues.`

### Model Architecture
![image](https://github.com/user-attachments/assets/a9da8c26-22aa-476c-afb6-2e1dbb5003d0)

- **EfficientNetB0 (Convolutional Feature Extractor):** Extracts hierarchical spatial features from the input spectrogram using depthwise separable convolutions.
- **Global Average Pooling Layer:** Aggregates the spatial feature maps into a single vector by computing the average of each feature map.
- **Dense Layer (1280 → 256):** Reduces dimensionality and learns important high-level features.
- **Dropout Layer (256 → 256):** Prevents overfitting by randomly deactivating neurons during training.
- **Dense Layer (256 → 1):** Final classification layer using a sigmoid activation function to produce the output.

