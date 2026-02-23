# Project Title: Machine Learning-Driven Predictive Modeling of Human Carbonic Anhydrase II Inhibitors

## Project Overview
Human Carbonic Anhydrase II is a critical enzyme involved in various physiological processes, including pH regulation and fluid secretion. It is a major drug target for glaucoma, edema, and epilepsy. This project demonstrates a complete Cheminformatics workflow—from data acquisition to predictive modeling by the classification of small-molecule inhibitors targeting Human Carbonic Anhydrase II (hCA II). By integrating high-throughput bioactivity data from the ChEMBL database with state-of-the-art machine learning algorithms, this project demonstrates how cheminformatics can accelerate the drug discovery process for targets associated with glaucoma, epilepsy, and altitude sickness.

The Pipeline The workflow begins with automated data acquisition and rigorous cleaning of ~1,200 compounds. Each molecule is featurized using Morgan Fingerprints (ECFP4)—a circular fingerprinting method that captures the essential pharmacophoric environments of the atoms.
We evaluate the structural-activity relationships through four distinct lenses:
Logistic Regression: Establishing a linear baseline for molecular similarity.
Support Vector Machines (SVM): Utilizing RBF kernels to map high-dimensional chemical space.
Random Forest & XGBoost: Leveraging ensemble learning to capture the complex, non-linear interactions between chemical functional groups and the hCA II active site.
Key Features * Robust Validation: Employs Stratified 5-Fold Cross-Validation to ensure model generalizability and prevent data leakage.
Advanced Analytics: Beyond simple accuracy, the project implements Precision-Recall (PR) Curves and ROC-AUC analysis, providing a nuanced view of model performance on imbalanced bioactivity datasets.
Reproducibility: Designed as a "one-click" executable environment in Google Colab, making sophisticated cheminformatics accessible to researchers and students alike.
Conclusion The results highlight the superior performance of ensemble methods (Random Forest/XGBoost) in identifying the specific sulfonamide-based motifs characteristic of potent hCA II inhibitors. This tool serves as a foundational framework for virtual screening and lead optimization in medicinal chemistry.

This project implements a machine learning pipeline to classify small molecule inhibitors of **Human Carbonic Anhydrase II (hCA II)**. By leveraging data from the ChEMBL database, we build and compare several models to predict whether a compound is "active" (IC₅₀ < 1 µM) or "inactive."

## Workflow Steps

### Step A — Data Acquisition
* **Source:** Data is programmatically retrieved from the **ChEMBL database** (Target ID: `CHEMBL205`).
* **Filtering:** We extract compounds with experimentally measured **IC₅₀** values.
* **Labeling:** Bioactivity values are converted into binary classes. 
    * **Active (1):** IC₅₀ < 1,000 nM (1 µM)
    * **Inactive (0):** IC₅₀ ≥ 1,000 nM

### Step B — Preprocessing & Featurization
* **SMILES Processing:** RDKit is used to parse Canonical SMILES strings.
* **Fingerprinting:** Molecules are featurized using **Morgan Fingerprints (ECFP4)** with a radius of 2 and 2,048 bits. This captures the local circular environment of atoms, essential for SAR (Structure-Activity Relationship) analysis.
* **Data Splitting:** The dataset is split into training (80%) and testing (20%) sets, using stratification to maintain class balance.

### Step C — Machine Learning Models
We implement and compare four distinct algorithms to benchmark performance:
1.  **Logistic Regression:** Serves as a linear baseline.
2.  **Random Forest:** An ensemble method to capture non-linear relationships.
3.  **SVM (RBF Kernel):** Effective for high-dimensional fingerprint data.
4.  **XGBoost:** A gradient boosting framework for high-performance classification.

## Evaluation
Models are evaluated using **Stratified 5-Fold Cross-Validation** to ensure robustness and avoid data leakage. Key metrics include:
* **ROC-AUC:** Measures the model's ability to distinguish between classes.
* **Accuracy:** Overall percentage of correct predictions.

## How to Run
You can run this project directly in your browser via Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Babakmamnoon/Machine-Learning-Driven-Predictive-Modeling-of-Human-Carbonic-Anhydrase-II-Inhibitors/blob/main/Machine_Learning_on_Human_Carbonic_Anhydrase_II_Inhibition.ipynb)


### Prerequisites
The script automatically installs the necessary dependencies:
* `rdkit`
* `chembl_webresource_client`
* `scikit-learn`
* `xgboost`
