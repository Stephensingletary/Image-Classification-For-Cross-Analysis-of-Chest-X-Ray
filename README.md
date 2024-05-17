# Image-Classification-For-Cross-Analysis-of-Chest-X-Ray

Project 3 for U of U AI Bootcamp. Upload your chest X-Ray using the included Gradio GUI to output likely clinical diagnosis. Not intended as medical advice.

Data sourced from here: https://www.kaggle.com/datasets/nih-chest-xrays/sample?resource=download


The process involves two main steps: Data Preparation and Image Preprocessing.

## Data Preparation (`data_prep.ipynb`)
In Data Preparation, the steps include importing necessary libraries, loading and cleaning data by processing age values, handling categorical labels through one-hot encoding, encoding other categorical data like gender and position, managing missing values, and performing a final data integrity check before saving the cleaned dataset.

## Image Preprocessing (`image_prep.ipynb`)
Image Preprocessing involves setting up the environment with required libraries, loading and verifying cleaned metadata, visualizing data to ensure accuracy, creating functions to process images (such as resizing and normalizing), and discussing potential adjustments like batch processing and efficient data storage.

Image processing updated