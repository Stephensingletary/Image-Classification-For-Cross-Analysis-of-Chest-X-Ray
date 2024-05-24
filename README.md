# Chest X-ray Disease Detection Project

## Overview

This project aims to develop a convolutional neural network (CNN) for detecting diseases in chest X-ray images using the NIH Chest X-ray dataset. The goal is to create a computer-aided detection and diagnosis system to assist radiologists in identifying common thoracic diseases.

## Dataset

### NIH Chest X-ray Dataset
- **Size**: 112,120 frontal-view X-ray images
- **Patients**: 30,805 unique patients
- **Diseases**: 14 common thoracic diseases including Atelectasis, Cardiomegaly, Effusion, Infiltration, Mass, Nodule, Pneumonia, Pneumothorax, Consolidation, Edema, Emphysema, Fibrosis, Pleural Thickening, and Hernia
- **Resolution**: 1024x1024 pixels
- **Metadata**: Includes patient details, image properties, and disease labels extracted using natural language processing (NLP)

## Data Processing

### Steps Involved:
1. **Data Loading**: Loaded data from `BBox_List_2017.csv` and `Data_Entry_2017.csv`.
2. **Image Paths**: Defined paths for image folders and created a DataFrame for image paths and indices.
3. **Data Merging**: Merged data from bounding box annotations and metadata with image paths.
4. **Data Balancing**: Balanced the dataset by undersampling the majority class (No Finding).
5. **One-Hot Encoding**: Converted 'Finding Labels' into a one-hot encoded format.
6. **Patient Age Cleaning**: Filtered and normalized patient ages.
7. **Categorical Encoding**: One-hot encoded 'Patient Gender' and 'View Position' columns.
8. **Dropping Unnecessary Columns**: Removed unnecessary columns from the data.
9. **Exploratory Data Analysis (EDA)**: Visualized the distribution of diseases and patient ages.
10. **Saving Cleaned Data**: Saved the cleaned data to CSV files for further use.

## Model Creation and Training

### Technologies Used:
- **TensorFlow**: For building and training the deep learning models.
- **Keras**: High-level API for TensorFlow, enabling easy model creation and training.
- **SciKit-Learn**: For data preprocessing, resampling, and computing class weights.
- **Pandas**: For data manipulation and analysis.
- **NumPy**: For numerical computations.
- **Matplotlib**: For data visualization.
- **PIL (Python Imaging Library)**: For image processing.

### Model Architecture:
- **Input Layer**: Image size 256x256 pixels
- **Convolutional Layers**:
  - Conv2D with 32 filters, kernel size 3x3, ReLU activation
  - Conv2D with 64 filters, kernel size 3x3, ReLU activation
  - Conv2D with 128 filters, kernel size 3x3, ReLU activation
  - Conv2D with 256 filters, kernel size 3x3, ReLU activation
- **Pooling Layers**: MaxPooling2D after each convolutional block
- **Fully Connected Layers**:
  - Dense layer with 256 neurons, ReLU activation
  - Dropout layer with a dropout rate of 0.5
- **Output Layer**: Dense layer with 1 neuron, sigmoid activation for binary classification

### Training Parameters:
- **Optimizer**: Adam
- **Learning Rate**: 0.001
- **Loss Function**: Binary Crossentropy
- **Batch Size**: 32
- **Epochs**: 10
- **Data Augmentation**: 
  - Rotation Range: 20 degrees
  - Width Shift Range: 0.2
  - Height Shift Range: 0.2
  - Horizontal Flip: True
- **Class Weights**: Computed to handle class imbalance

## Evaluation Results

### Performance Metrics:
- **Test Accuracy**: 0.5023
- **Test Loss**: 0.6965
- **Classification Report**:
  - **No Finding**:
    - Precision: 0.00
    - Recall: 0.00
    - F1-score: 0.00
    - Support: 10,304
  - **Finding**:
    - Precision: 0.50
    - Recall: 1.00
    - F1-score: 0.67
    - Support: 10,400
  - **Overall Accuracy**: 50.23%
  - **Macro Average**:
    - Precision: 0.25
    - Recall: 0.50
    - F1-score: 0.33
  - **Weighted Average**:
    - Precision: 0.25
    - Recall: 0.50
    - F1-score: 0.34

### Observations:
- The current model shows a test accuracy of approximately 50%, indicating it correctly classifies half of the instances.
- The precision, recall, and F1-score for the 'No Finding' class are very low, indicating the model is not effectively identifying images without findings.
- The model performs better for the 'Finding' class with a recall of 1.00, suggesting it classifies all 'Finding' instances correctly, but this comes at the expense of many false positives.

### Challenges and Future Steps:
- **Local CPU Limitation**: Training the model on a local CPU took around 5 hours, which is a significant limitation due to the large dataset size (approximately 45GB).
- **Cloud Training**: Given the dataset's size, training on local machines is impractical for obtaining optimal results. We are continuing to train the model on Google Cloud Services, which provides the necessary computational resources to handle such a large dataset efficiently.

### Conclusion:
While the current model's performance is not satisfactory, we have established a baseline that can be further developed. Transitioning the training process to a cloud-based environment will allow us to leverage more powerful computational resources, leading to more accurate and reliable results. The model will continue to be refined, and we expect to achieve satisfactory performance in the near future.

---
