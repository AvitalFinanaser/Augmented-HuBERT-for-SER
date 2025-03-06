# Augmented-HuBERT-for-SER
Enhancing HuBERT's Speech Emotion Recognition through Data Augmentation and Fine-tuning.

## Overview
This project investigates how various data augmentation techniques can enhance the robustness of HuBERT-based Speech Emotion Recognition (SER) models. We examine four key augmentation methods—Time Stretch, Additive Noise, SpecAugment, and Natural Copy-paste (N-CP) — individually and in probability-weighted combinations to determine optimal configurations for improving model performance and generalization.

## Background
Speech Emotion Recognition (SER) systems often struggle with real-world variability in acoustic conditions and speaker characteristics. Pre-trained models like HuBERT show promising performance in controlled environments but may lack robustness when deployed in diverse settings. Data augmentation offers a promising approach to address these limitations without requiring extensive additional data collection or radical model architecture changes.

## Repository Structure

- **notebooks**: Contains implementation code executed in the Google Colab environment. The notebooks in the repository are designed to run in Colab and include the necessary setup steps, including the needed project drive path. 
- **data**: Includes cleaned RAVDNESS and SAVEE datasets.
- **assets**: Contains summary visualizations.
- **models**: Stores our 8 trained models, managed using Git LFS for efficient storage.

## Datasets
The project uses two emotional speech datasets:
- **RAVDESS** (Ryerson Audio-Visual Database of Emotional Speech and Song)
  - Primary dataset for training and initial evaluation
  - Contains recordings from 24 professional actors (12 female, 12 male)
  - High-quality studio recordings

- **SAVEE** (Surrey Audio-Visual Expressed Emotion)
  - Used for cross-dataset validation to assess generalization
  - Recordings from 4 male actors
  - Provides a test for model robustness across different recording conditions and speaker characteristics

## Methodology

Our approach examines how data augmentation can enhance a pre-trained HuBERT model that uses WAV2VEC2 for feature extraction from WAV audio files:

### Stage 1. Baseline Model Establishment
- **Model Configuration**: Adaptation of pre-trained "superb/hubert-large-superb-er" model for seven emotion categories
- **Feature Extraction**: Implementation of WAV2VEC2 for audio feature representation
- **Performance Assessment**: Evaluation of model accuracy on clean RAVDESS test set
- **Metrics Documentation**: Comprehensive recording of performance across emotion categories

### Stage 2.  Data Augmentation Methods
- **Time Stretch Development**: Implementation of speech rate modification while maintaining pitch integrity
- **Additive Noise Integration**: Creation of environmental noise injection framework with controlled signal-to-noise ratios
- **SpecAugment Application**: Development of frequency and time masking procedures for spectral augmentation
- **Copy-Paste Methodology**: Establishment of segment combination techniques for emotional utterance synthesis
- **Dataset Generation**: Creation of augmented datasets with 1:1 ratio to original data

### Stage 3.  Single-Method Model Training
- **Individual Training Procedure**: Training of separate models using each augmentation technique
- **Clean Test Evaluation**: Assessment of model performance on unmodified test data
- **Augmented Test Assessment**: Analysis of model robustness on augmented test sets
- **Performance Comparison**: Identification of relative effectiveness across augmentation techniques

### Stage 4. Combined Augmentation Models
- **Weighted Combination Formulation**: Development of probability-weighted combinations based on individual F1-score gains
- **Systematic Configuration Exploration**: Analysis of various weighting schemes for optimal performance
- **Multi-method Model Creation**: Implementation of three combination strategies - Top2, Top3, Top4
- **Comprehensive Model Development**: Integration of all four techniques with optimized probability weights
- **Probability-weighted Selection**: Implementation of sampling mechanism favoring higher-performing techniques
- **Evaluation Framework**

### Stage 5. Cross-Dataset Validation
- **External Dataset Selection**: Utilization of SAVEE dataset with matching emotional categories
- **Generalization Assessment**: Evaluation of top-performing models on an unseen dataset
- **Comparative Analysis**: Quantification of improvement over baseline model
- **Robustness Measurement**: Assessment of model performance across varied acoustic conditions

## Key Findings

* Frequency domain augmentations, particularly SpecAugment, proved most effective in preserving emotional markers while enhancing model robustness, especially for angry and fearful emotions.
* The SpecAugment+TimeStretch combination demonstrated complementary benefits by targeting both frequency and temporal domains, achieving balanced performance across emotions.
* Cross-corpus validation revealed persistent challenges, with substantial performance gaps indicating augmentation alone cannot bridge fundamental acoustic differences between datasets with distinct speaker demographics.

These findings establish a framework for emotion-specific augmentation selection while highlighting the need for more sophisticated cross-corpus generalization approaches.

## Contributors
Avital Finanser & Sivan Raviv-BenZvi.

## Acknowledgments
This project was completed as part of Introduction to Deep Learning course at IEM Department, at Ben-Gurion University of the Negev, under the guidance of Ari Pakman, 2025.
