# Ray-Distributed-Training

# Student Performance Risk Classification with Distributed Training using Ray

This repository contains a Colab notebook that builds a three-level student risk classifier using Ray for distributed training and PyTorch for model development. The project uses the Student Performance dataset and assigns each student to one of three risk categories based on grades, failures, and absences.

The repository includes:
- The Colab notebook with outputs  
- The dataset file  
- This README

---

## 1. Project Overview

The notebook demonstrates the end-to-end workflow for preparing data, performing exploratory data analysis, preprocessing features, generating risk labels, training an MLP classifier, and running the training loop using Ray's distributed training framework.

The model predicts:
- Low risk  
- Medium risk  
- High risk  

The risk level is derived from the dataset using rule-based thresholds involving final grade (G3), number of past failures, and absences.

---

## 2. Notebook Structure

### 2.1 Imports and Environment Setup
Loads required libraries including Ray, PyTorch, Pandas, and supporting modules.

### 2.2 Data Upload
The dataset is uploaded from the local system into Colab for processing.

### 2.3 Exploratory Data Analysis
The dataset is inspected for structure, data types, missing values, distributions, and correlations.  
This section produces summary tables and basic plots.

### 2.4 Dataset Preprocessing
A preprocessing function converts the raw dataset into:
- A feature matrix containing selected numeric columns  
- A target vector containing risk labels (low, medium, high)

The dataset is then converted into a Ray Dataset for distributed processing.

### 2.5 Model Definition
A simple three-layer MLP classifier is defined using PyTorch.

### 2.6 Distributed Training with Ray
Ray’s `TorchTrainer` is configured and executed.  
This includes:
- Dataset sharding  
- GPU detection  
- Training loop with batch processing  
- Validation accuracy reporting per epoch  

### 2.7 Training Summary
A final local training pass is run to produce a clear summary table of:
- Epoch  
- Training loss  
- Validation accuracy  

This table is displayed at the end of the notebook.

---

## 3. Dataset

The project uses the `student-mat.csv` dataset containing student academic and social information.  
Key numeric features used include:
- Age  
- Parental education  
- Travel time  
- Study time  
- Past failures  
- Family relations  
- Free time  
- Social activity  
- Alcohol consumption  
- Health  
- Absences  
- Period grades G1 and G2  

The dataset file is included in this repository for reproducibility.

---

## 4. Running the Notebook

### 4.1 Using Google Colab
1. Open the notebook in Colab.  
2. Upload the dataset when prompted.  
3. Execute all cells in sequence.

### 4.2 Running Locally
To run locally, install the dependencies:

pip install ray[default] torch torchvision pandas matplotlib


GPU support requires a compatible CUDA installation.

---

## 5. Viewing the Notebook on GitHub

GitHub may not always render `.ipynb` files that were generated in Colab due to metadata constraints.  
For consistent viewing, the repository includes an HTML export of the notebook with full outputs.

To view it:
- Open the `.html` file directly in GitHub  
- Or download and open it in a browser  

---

## 6. Files in This Repository

- `notebook.ipynb` – Full Colab notebook  
- `student-mat.csv` – Dataset used  
- `README.md` – Documentation  

---

## 7. Notes

The notebook demonstrates:
- Dataset preprocessing with Ray  
- Parallelized transformation using `map_batches`  
- Distributed training using `TorchTrainer`  
- Evaluation of model performance  
- A summary table generated outside Ray for clear reporting  

---

