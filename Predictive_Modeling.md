# Student Performance Predictions

## Objective
This project aims to explore student performance based on data from two datasets: `student-mat.csv` and `student-por.csv`. The analysis predicts student success in math and Portuguese using classification techniques, clustering, and a multi-output neural network.

---

## Tools and Libraries
- Python
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`, `tensorflow`

---

## Key Steps

### 1. Data Preprocessing
- Merged datasets on shared columns.
- Dropped irrelevant columns and performed one-hot encoding for categorical variables.
- Generated new features, e.g., `Weekly_Alc_Consumption`.

### 2. Exploratory Data Analysis (EDA)
- Created heatmaps and distribution plots to study feature correlations.
- Focused on predictors with correlations < 0.7 to avoid multicollinearity.

### 3. Classification Models
- **Models**: Decision Tree, K-Nearest Neighbors, Logistic Regression, Random Forest.
- **Features**: Used all relevant predictors except target grades (`G3_math`, `G3_port`).
- **Targets**: Converted grades into binary pass/fail categories (threshold = 10).

#### Model Performances:
- **Decision Tree**: 72.7% (Math), 89.6% (Portuguese)
- **K-Nearest Neighbors**: 66.2% (Math), 88.3% (Portuguese)
- **Logistic Regression**: 76.6% (Math), 90.9% (Portuguese)
- **Random Forest**: 81.8% (Math), 90.9% (Portuguese)


---

### 4. Multi-Output Neural Network
- **Architecture**: Shared hidden layer with separate output layers for math and Portuguese predictions.
- **Metrics**: Mean Absolute Error (MAE).

---

### 5. Clustering Analysis
- Performed K-Means clustering on:
  - Weekly Alcohol Consumption vs. Final Math Grade
  - Weekly Alcohol Consumption vs. Final Portuguese Grade
- Visualized clusters and their centroids.

---

## Results and Insights
- Logistic Regression and Random Forest outperformed other models.
- Alcohol consumption had a noticeable impact on student grades.
- Neural networks achieved reasonable MAE scores, though traditional models performed better for classification.

---

## Visualizations
- Heatmaps for feature correlations.
- Histograms for data distribution.
- Scatter plots for clustering results.

---

## Code Highlights
```python
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

# Logistic Regression
lr_classifier = LogisticRegression(random_state=42)
lr_classifier.fit(X_train_math, y_train_math)
math_preds = lr_classifier.predict(X_test_math)
accuracy = accuracy_score(y_test_math, math_preds)
print(f"Logistic Regression Accuracy (Math): {accuracy}")
```

---

## Future Work
- Experiment with advanced neural network architectures.
- Incorporate additional datasets for broader insights.
- Fine-tune hyperparameters for clustering models.

---
