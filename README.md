# Dry Beans Classifier TODO: Finish README

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)]()
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)]()
[![Seaborn](https://img.shields.io/badge/seaborn-%233776AB.svg?style=for-the-badge&logoColor=white)]()

## 📌 Project Overview
This project focuses on building and evaluating classification models using the Dry Bean dataset[cite: 4]. The primary objective is to accurately classify seven distinct species of dry beans ('SEKER', 'BARBUNYA', 'BOMBAY', 'CALI', 'HOROZ', 'SIRA', 'DERMASON') based on their geometric and morphological features.

## 📂 Dataset & Scope
*   **Source:** UC Irving - Machine Learning Repository -> [Dry Beans](https://archive.ics.uci.edu/dataset/602/dry+bean+dataset)
*   **Scope:** The dataset was filtered to focus exclusively on the predictability of 2 features -> `Extent` and `ConvexArea`.

## 🚀 Methodology

### Data Strategy
*   **Dataset:** 13,611 instances with 16 numeric features and 1 categorical target (`Class`).
*   **Partitioning:** The data was split into three sets: Training (70%), Validation (20%), and Testing (10%).
*   **Stratification:** `stratify=y` was used during splitting to preserve the class distribution across all partitions, ensuring minority classes are adequately represented and model evaluation remains stable.
*   **Scaling:** `StandardScaler` was fitted strictly to the training data and used to transform the validation and test sets. This step was critical for distance-based algorithms, preventing large-scale features (like `ConvexArea`) from overwhelming smaller-scale features (like `Extent`)

### Models Evaluated
1.  **k-Nearest Neighbors (kNN):** Evaluated on both scaled and unscaled data to observe the impact of standardization. Hyperparameter tuning was performed for $k \in \{3, 5, 7, 9\}$.
2.  **Linear Discriminant Analysis (LDA) & **Quadratic Disriminant Analysis (QDA)** :** A generative multimodel approach using a shared covariance matrix assumption.
3.  **Gaussian Naive Bayes (GNB):** A generative model evaluating feature independence.

## 📊 Key Findings & Evaluation
*   **kNN Performance:** The kNN algorithm is highly sensitive to feature scaling[cite: 4]. The baseline unscaled kNN ($k=5$) yielded a validation accuracy of 57.57%. After applying `StandardScaler`, validation accuracy improved significantly to 65.06%. 
*   **Optimal Hyperparameters:** Hyperparameter tuning revealed that $k=9$ provided the best performance, achieving a validation accuracy of 67.16% and a final test accuracy of 67.33%. The close alignment between validation and test scores indicates that the model generalized well without overfitting.
*   **LDA Performance:** The Linear Discriminant Analysis model achieved a validation accuracy of 60.32%.

## Requirements
*   Python 3.x
*   NumPy
*   Pandas
*   Matplotlib / Seaborn
*   Scikit-Learn (KNeighborsClassifier, LinearDiscriminantAnalysis, GaussianNB, StandardScaler, LabelEncoder)

## 🛠️ How to Run the Project
1. Clone the repository:
   ```bash
   git clone [https://github.com/Bobby-Bag/dry-beans-classification-model.git](https://github.com/Bobby-Bag/dry-beans-classification-model.git)
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
3. Run the Jupyter Notebook to view the EDA, feature selection, and model evaluation.
