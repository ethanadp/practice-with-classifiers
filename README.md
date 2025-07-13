# Bank Marketing Campaign Modeling and Client Targeting

This project applies the CRISP-DM framework to a real-world dataset from a Portuguese bank to build predictive models that identify which clients are most likely to subscribe to a term deposit. The final output is designed to help banks improve their telemarketing campaign efficiency, reduce costs, and increase conversion rates.

---

## Business Objective

The bank wants to reduce the number of calls needed during telemarketing campaigns while still achieving high subscription rates for term deposits. The goal of this project is to build classification models that can predict whether a client will subscribe, enabling the bank to prioritize high-potential leads.

---

## Dataset

- Source: [UCI Machine Learning Repository – Bank Marketing Data Set](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)
- Records: 41,188 marketing contacts
- Target: `y` (binary — yes/no subscription)
- Key Features: `job`, `marital`, `education`, `pdays`, `previous`, `euribor3m`, `contact`, `month`, etc.

---

## Process Overview (CRISP-DM)

### 1. Business Understanding
Defined the bank's need to improve efficiency in direct marketing by predicting term deposit subscriptions.

### 2. Data Understanding
Performed:
- Data type inspection and feature categorization
- Detection of 'unknown' and proxy-missing values
- Class balance analysis (target distribution: ~11% 'yes')

### 3. Data Preparation
- Removed `duration` (leaks target and is unusable in live scenarios)
- Imputed 'unknown' with mode values
- One-hot encoded categorical features
- Scaled numeric features using `StandardScaler`
- Stratified train/test split (70/30)

### 4. Modeling
Tested:
- **Logistic Regression** (Best Performer)
- **K-Nearest Neighbors (KNN)**
- **Decision Tree**
- **Support Vector Machine (SVM)**

### 5. Evaluation
| Model              | Best Params             | Train Accuracy | Test Accuracy | Train Time (s) |
|--------------------|--------------------------|----------------|----------------|----------------|
| Logistic Regression | C = 0.1                  | 0.8997         | 0.9022         | 0.07           |
| KNN                | n_neighbors = 7          | 0.9086         | 0.8969         | 0.00           |
| Decision Tree      | max_depth = 3            | 0.8993         | 0.9012         | 0.02           |
| SVM                | C = 1, kernel = 'rbf'    | 0.9095         | 0.9005         | 19.40          |

- Logistic Regression offered the best mix of performance and efficiency.
- KNN performed decently but was slightly less stable on test data.
- Decision Trees started to overfit at deeper depths.
- SVM came close in accuracy but required significant training time.

### 6. Deployment
Prepared final model summary and visualizations for:
- Class distribution and baseline accuracy
- Feature dimensionality before and after encoding
- Model accuracy and timing comparison
- Grid search performance across hyperparameters

---

## Key Insights

- Most categorical variables like `job` and `education` required imputation before modeling.
- Logistic Regression worked well, suggesting the decision boundary is mostly linear.
- SVM offered similar performance but at a much higher computational cost.
- Decision Trees are interpretable but prone to overfitting if not pruned properly.
- Class imbalance (only ~11% positive class) makes the baseline deceptively high.

---

## Visual Highlights

- Target class pie chart
- Bar plots of categorical feature distributions
- Dimensionality growth post one-hot encoding
- Model comparison bar charts (accuracy, train time)
- Grid search visualization of parameter tuning

---

## Files

- `bank_marketing_notebook.ipynb` — Main notebook with full CRISP-DM pipeline
- `bank-additional-full.csv` — Original dataset
- `README.md` — Project summary and usage guide

---
