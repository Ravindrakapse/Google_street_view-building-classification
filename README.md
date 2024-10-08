﻿\# Project Overview

This project focuses on building classification using YOLOv8n for outlier detection and classification of building types. The process is divided into two main steps:

1. \*\*Preprocessing\*\*: Detecting and removing outliers from the raw data.
1. \*\*Classification\*\*: Training and evaluating the model on the preprocessed data for building type classification.

The repository is organized into two folders:

1. \*\*Preprocessing\_MLCPS\*\*: This folder is for outlier detection, where each class (A, B, C, D, S) has its own YOLO setup.
1. \*\*YOLO\_MLCPS\*\*: This folder is for the classification of preprocessed data.

\## Folder Structure

\### 1. Preprocessing\_MLCPS (Outlier Detection)

This folder contains the code and data required to perform outlier detection using YOLO. Each class (A, B, C, D, S) is stored in a separate folder with a similar structure.

- \*\*Folder Structure\*\*:

\```

Preprocessing\_MLCPS/

├── yolo\_A/

│   ├── config.yaml            # YOLO configuration file for class A

│   ├── train.ipynb            # Notebook for training YOLO on class A data

│   ├── data/

│   │   ├── images/

│   │   │   ├── train/         # Training images for class A

│   │   │   └── val/           # Validation images for class A

│   │   ├── labels/

│   │   │   ├── train/         # Corresponding labels (.txt files) for training images

│   │   │   └── val/           # Corresponding labels (.txt files) for validation images

├── yolo\_B/

├── yolo\_C/

├── yolo\_D/

├── yolo\_S/

\```

- \*\*Steps to Run Outlier Detection\*\*:
1. Navigate to the specific folder for each class (e.g., `yolo\_A`, `yolo\_B`).
1. Open the `train.ipynb` file and ensure that the paths are set correctly for images and labels.
1. Modify the `config.yaml` file to match the correct folder structure.
1. Run the notebook to detect and remove outliers.

\### 2. YOLO\_MLCPS (Classification)

This folder is for the classification of building types using the preprocessed data. The folder structure follows YOLO’s requirements for training and validation.

- \*\*Folder Structure\*\*:

\```

YOLO\_MLCPS/

├── train/                   # Contains training images with class subfolders

│   ├── A/

│   ├── B/

│   ├── C/

│   ├── D/

│   └── S/

├── val/                     # Contains validation images with class subfolders

│   ├── A/

│   ├── B/

│   ├── C/

│   ├── D/

│   └── S/

├── yolo\_imagenet.ipynb      # Notebook for training the classification model

├── runs/

│   ├── classify/

│   │   ├── train/

│   │   │   ├── weights/

│   │   │   │   └── best.pt  # Trained YOLOv8n-cls model

├── submission\_yolo\_detected.csv  # Submission file for Kaggle leaderboard

\```

- \*\*Steps to Train the YOLO Classification Model\*\*:
1. Open the `yolo\_imagenet.ipynb` file.
1. Ensure that the paths for training and validation data are set correctly in the notebook.
1. Modify any necessary hyperparameters for training, such as epochs, etc.
1. Run the notebook to train the YOLOv8n-cls model.
1. The trained model weights will be saved under `runs/classify/train/weights/best.pt`.

- \*\*Submission\*\*:
- The file `submission\_yolo\_detected.csv` is the output generated from the YOLO model, which was submitted on Kaggle and ranked on the leaderboard.

\## Instructions

\### Requirements

To run the project, ensure the following dependencies are installed:

- Python 3.x
- TensorFlow / Keras
- ultralytics (for YOLOv8n)
- Scikit-learn
- Matplotlib
- NumPy, Pandas




\### Files Description for ResNet

- \*\*ResNet\_MLCPS.ipynb\*\*:
- This Jupyter notebook contains the code to train and validate the ResNet50 model on the building dataset. It uses transfer learning with a pre-trained model (ImageNet) and includes data preprocessing and augmentation steps.
- The notebook will load the dataset, apply preprocessing (resizing images to 244x244), and train the ResNet model. After training, it saves the best model weights (`ResNet244\_detected.h5`).

- \*\*ResNet244\_detected.h5\*\*:
- This is the saved model file containing the best weights from the training process.
- You can load this model directly for inference or further fine-tuning.

\### How to Use

1. \*\*Requirements\*\*:

Ensure the following libraries are installed:

- TensorFlow / Keras
- NumPy, Pandas
- Matplotlib


2\. \*\*Training\*\*:

- Open the `ResNet\_MLCPS.ipynb` file in Jupyter Notebook or Google Colab.
- Ensure the dataset path is correctly set up inside the notebook.
- Run the notebook to train the ResNet50 model.
- The best model weights will be saved as `ResNet244\_detected.h5` after training.

3\. \*\*Model Inference\*\*:

- You can load the trained model (`ResNet244\_detected.h5`) using Keras' `load\_model` function to perform predictions on new data.

\```python

from tensorflow.keras.models import load\_model

model = load\_model('ResNet244\_detected.h5')
