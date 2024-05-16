# Image-Classification-For-Cross-Analysis-of-Chest-X-Ray

Project 3 for U of U AI Bootcamp. Upload your chest X-Ray using the included Gradio GUI to output likely clinical diagnosis. Not intended as medical advice.
# Project Overview: NIH Chest X-Ray Dataset

This project involves the use of the NIH Chest X-Ray Dataset to develop a machine learning model capable of diagnosing medical conditions from x-ray images. The project is divided into two main parts: data preparation and image preprocessing, detailed in two separate Jupyter notebooks.

## Data Preparation (`data_prep.ipynb`)

### Steps Performed:

1. **Import Libraries**: Essential libraries such as pandas and os are imported to facilitate data manipulation and path operations.

2. **Load Data**: The dataset `sample_labels.csv` is loaded into a pandas DataFrame to access the metadata associated with x-ray images.

3. **Age Processing**:
   - Convert 'Patient Age' from string to integer.
   - Remove non-digit characters.
   - Handle and remove age outliers that are not physiologically plausible (e.g., ages above 120).

4. **Label Handling**:
   - Transform 'Finding Labels' from concatenated strings to lists for easier processing.
   - Implement one-hot encoding using `MultiLabelBinarizer` to convert disease labels into a binary format suitable for model training.

5. **Encode Categorical Data**:
   - Encode 'Patient Gender' and 'View Position' using `LabelEncoder` to transform these categorical variables into numerical codes.

6. **Missing Values**:
   - Identify and remove any rows with missing data to maintain dataset integrity.

7. **Data Integrity Check and Save**:
   - Perform a final check on the cleaned data, review statistics, and save the cleaned dataset to a new CSV file, `sample_labels_cleaned.csv`.

## Image Preprocessing (`image_prep.ipynb`)

### Steps Performed:

1. **Set Up Environment**:
   - Import necessary libraries including TensorFlow, Keras, and PIL for image operations.

2. **Load and Verify Data**:
   - Load the cleaned metadata and verify the structure.
   - Append paths to image files based on the metadata.

3. **Visualize Images and Metadata**:
   - Display images along with their corresponding metadata to confirm correct loading and alignment.

4. **Image Preprocessing Functions**:
   - Develop functions to resize, normalize, and optionally augment image data using `ImageDataGenerator`.
   - Visualize the effects of preprocessing and augmentation on sample images.

5. **Additional Considerations**:
   - Discuss potential adjustments for specific project needs such as batch processing, caching preprocessed images, and saving processed data efficiently.

## Summary

The project sets up a comprehensive preprocessing pipeline for both metadata and image data, ensuring that the data is clean, well-formatted, and ready for the next stages of model training and evaluation. The preprocessing steps address issues such as data cleanliness, categorical encoding, and image file handling, which are crucial for the successful application of machine learning techniques in medical diagnostics.
