# Salary Estimation Project

## Objective
This project analyzes salary data for various job roles to estimate salaries using machine learning techniques. The data undergoes preprocessing, exploratory analysis, and model-building to identify salary determinants.

---

## Tools and Libraries
- Python
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`

---

## Key Steps

### 1. Data Preprocessing
- Cleaned and formatted the dataset:
  - Removed irrelevant columns like `Headquarters` and `Revenue`.
  - Standardized numerical features (e.g., `age`, `avg_salary`).
  - Imputed missing values with median values.
  - Created one-hot encodings for categorical features like `Type of ownership` and `job_state`.

### 2. Exploratory Data Analysis (EDA)
- Visualized relationships between key features and average salary.
- Heatmap displayed feature correlations to address multicollinearity.

#### Key Insights:
- Features like `desc_len`, `Rating`, and `age` are significant predictors of salary.

---

### 3. Classification Models
- **Models**: Decision Tree and Logistic Regression.
- **Target**: Binary classification for salaries above or below the mean salary.

#### Model Performances:
| Model                | Accuracy |
|----------------------|----------|
| Decision Tree        | 81.6%    |
| Logistic Regression  | 69.5%    |

- **Feature Importances (Decision Tree):**
  - `desc_len`: 23.3%
  - `Rating`: 15.6%
  - `age`: 10.4%

---

### 4. Clustering Analysis
Performed K-Means clustering to identify patterns in:
- **Age vs. Average Salary**: Clustered job categories based on company age and salary.
- **Description Length vs. Average Salary**: Highlighted variations in job description and salary.
- **Rating vs. Average Salary**: Examined how company ratings correlate with salary.

#### Results:
| Features                  | Clusters | SSE (Sum of Squared Errors) |
|---------------------------|----------|-----------------------------|
| Age vs. Avg Salary        | 2        | 1,646,680                  |
| Desc Length vs. Avg Salary| 3        | 334,113,895               |
| Rating vs. Avg Salary     | 3        | 224,169                   |

---

## Visualizations
- Scatter plots for feature comparisons (e.g., `desc_len` vs. `avg_salary`).
- Heatmaps to showcase feature correlations.
- Clustering results with centroids labeled.

---

## Code Highlights
```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score

model = DecisionTreeClassifier(random_state=42)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
print(f"Decision Tree Accuracy: {accuracy}")
```

---

## Future Work
- Include additional features like job descriptions and company sectors.
- Experiment with advanced models (e.g., Gradient Boosting, XGBoost).
- Evaluate clustering results with different metrics.

---


