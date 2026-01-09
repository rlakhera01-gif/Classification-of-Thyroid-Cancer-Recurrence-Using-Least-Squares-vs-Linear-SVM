# Classification of Thyroid Cancer Recurrence  
### Least Squares vs Linear SVM

Thyroid cancer recurrence prediction is an important clinical problem, as early identification of high-risk patients can support timely follow-up and improved treatment planning.

This project builds a machine learning pipeline to predict **thyroid cancer recurrence** and compares the performance of **Least Squares (Linear Regression used as a classifier)** and **Linear Support Vector Machine (Linear SVM)** models under class imbalance.

---

## Problem Statement

The objective of this project is to predict whether a patient will experience **thyroid cancer recurrence** based on clinical and pathological features.

This is framed as a **binary classification problem**, where:
- `1` → Cancer recurrence  
- `0` → No recurrence

---

## Dataset

- Source: Differentiated Thyroid Cancer Recurrence dataset  
- Observations: 383 patient records
- Target variable: `Recurrence`
- Feature types:
  - Demographic attributes
  - Tumor and pathology characteristics
  - Treatment-related variables

---

## Methodology

Two linear models are evaluated and compared:

### 1) Least Squares (Regression → Classification)
- A Linear Regression model is trained on the dataset.
- Continuous predictions are converted into class labels using a fixed threshold.
- Serves as a simple and interpretable linear baseline.

### 2) Linear Support Vector Machine (Linear SVM)
- A LinearSVC classifier is trained using a preprocessing and modeling pipeline.
- Hyperparameter `C` is tuned using **inner 5-fold cross-validation**.
- Class imbalance is handled using **balanced class weights**.

---

## Data Preprocessing

- Numerical features are scaled prior to modeling  
- Categorical features are encoded using one-hot encoding  
- Preprocessing and modeling are combined using **scikit-learn Pipelines** to ensure consistency during cross-validation

---

## Evaluation Strategy

- Primary evaluation metric: **Balanced Accuracy**
- Metric chosen to account for class imbalance in recurrence outcomes
- Final performance is reported using **5-fold cross-validation** on the finalized models

---

## Results

| Model | Balanced Accuracy (5-Fold CV) |
|------|-------------------------------|
| Least Squares | **0.925 ± 0.034** |
| Linear SVM | **0.945 ± 0.024** |

**Key observations:**
- Linear SVM achieves higher balanced accuracy and lower variance across folds.
- Improved recall for the recurrence class reduces false negatives.
- Least Squares remains interpretable but shows limitations in separating binary classes.

> Confusion matrices and detailed classification reports are available in the notebook and presentation.

---

## Repository Contents

- `notebooks/Thyroid_Recurrence_LS_vs_SVM.ipynb`  
  End-to-end analysis including preprocessing, modeling, and evaluation
- `data/Thyroid_Diff.csv`  
  Dataset used for training and evaluation
- `reports/Thyroid_Recurrence_LS_vs_SVM.pptx`  
  Presentation summarizing methodology and results

---

## Tech Stack

- Python
- NumPy
- Pandas
- scikit-learn
- Matplotlib
- Jupyter Notebook
