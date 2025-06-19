# IBM-HR-Analytics-Employee-Attrition-Performance

## Project Type: Data Analyst & Data scientist

## Project Owerview
This project analyzes employee data to predict attrition (whether an employee will leave) and uncover key factors influencing employee satisfaction, performance, and retention.
The objective is to help HR departments take proactive steps to reduce attrition and retain high-performing talent using data-driven insights and machine learning models.

* Analyzed IBM’s fictional HR dataset with 1,470 employee records
* Built machine learning models to predict employee attrition
* Conducted deep EDA and feature engineering to extract HR insights
* Used SHAP (SHapley Additive Explanations) to interpret model predictions
* Identified top predictors of attrition and actionable HR strategies

## Tools & Technologies
| Category               | Tools Used                                               |
|------------------------|----------------------------------------------------------|
| Programming Language   | Python 3                                                 |
| Data Manipulation      | Pandas, NumPy                                            |
| Visualization          | Matplotlib, Seaborn, SHAP                                |
| Machine Learning       | Scikit-learn, RandomForest                               |
| Explainability         | SHAP (TreeExplainer, Summary Plots, Dependence Plots)    |
| Jupyter Environment    | Google Colab                                             |


## Data Preprocessing & Feature Engineering
### Preprocessing
* Removed irrelevant columns (`EmployeeCount`, `Over18`, `EmployeeNumber`, etc.)
* Handled class imbalance and encoded categorical variables using `LabelEncoder`
* Scaled numerical features using `StandardScaler`

### 🔹 Feature Engineering
* `SatisfactionIndex`: Average of Job, Environment, Relationship, and WorkLife satisfaction
* `LoyaltyIndex`: Ratio of `YearsWithCurrManager` to `YearsAtCompany`
* `FastPromoted`: Flag if promotion occurred within 2 years
* `IncomeBucket`: Binned `MonthlyIncome` into 5 categories (Very Low to Very High)
* `AgeGroup`: Age categorized into `<25`, `25–35`, `35–45`, `45–55`, `55+`

These engineered features significantly improved model interpretability and performance.

## Advanced EDA with Screenshorts
### 1. Attrition Distribution
![EDA 1](https://github.com/user-attachments/assets/bdda04d1-f87d-4d7c-8a80-362f05f393fc)

* Found ~16% of employees left the company (class imbalance).
* Important for ML: shows need for class-balancing techniques.

### 2. Attrition by Department
![EDA 2](https://github.com/user-attachments/assets/0f8edbf7-8ad1-4e83-b706-959c7c37657b)

* Sales and HR departments had the highest attrition rates.
* R&D had the lowest, suggesting better retention practices.

### 3. Attrition by Job Role
![EDA 3](https://github.com/user-attachments/assets/f2178778-aa1b-4bb1-b604-2d6d3c5e081f)

* Sales Representatives and Lab Technicians showed significantly higher attrition.
* Roles like Research Director and Manager had much lower attrition rates.

### 4. Attrition by Gender
![EDA 4](https://github.com/user-attachments/assets/12f6f004-01a9-466a-85a9-2c8595900e8d)

* Slightly higher attrition among males, but the difference was minor.
* Suggests gender may not be a strong standalone predictor.

### 5. Monthly Income vs Attrition (Violin Plot)
![EDA 5](https://github.com/user-attachments/assets/9a4f1029-f28e-4743-99f5-d1707a5cf9b6)

* Employees who left generally had lower income.
* Showed income clustering among those who stayed (wider spread for "No").

### 6. Top Correlations with Attrition (Heatmap)
![EDA 6](https://github.com/user-attachments/assets/69c4a636-8868-412d-ae24-3610d1718e07)

* Key negative correlations:
  * YearsAtCompany, JobLevel, MonthlyIncome, SatisfactionIndex
* Positive correlation:
  * OverTime and NumCompaniesWorked 


## SHAP Visualizations Summary
![Shap_All_Plots](https://github.com/user-attachments/assets/6f3da94b-3e60-40d7-b7de-ae9abf739297)

### 1. SHAP Feature Importance (Bar Plot)
* Ranks features by their average impact on predicting attrition.
* Top predictors: OverTime, SatisfactionIndex, MonthlyIncome, StockOptionLevel.
* Helps identify which features the model relies on most globally.

### 2. SHAP Beeswarm Plot
* Visualizes the distribution of SHAP values for all features across all predictions.
* Red = high feature value, Blue = low feature value.
* Shows how and in what direction each feature affects the model's output.
* Example: High OverTime (red) consistently pushes toward attrition.

### 3. SHAP Force Plot (Single Prediction)
* Explains why the model predicted attrition for one employee.
* Red bars = features pushing prediction toward leaving.
* Blue bars = features pushing toward staying.
* Useful for case-by-case HR decisions and risk profiling.

### 4. SHAP Dependence Plot
* Shows how the SHAP value of one feature depends on its value and interacts with another feature.
* Example:
  * MonthlyIncome SHAP value depends heavily on JobSatisfaction.
  * Low income + low satisfaction → highest attrition risk.
* Reveals non-linear interactions and policy opportunities.




# Final Insights & Recommendations
## Insights

### 1. Top Predictors of Attrition
According to SHAP values:

* OverTime, SatisfactionIndex, MonthlyIncome, and LoyaltyIndex are the most influential features.

* Low SatisfactionIndex (avg. of 5 satisfaction metrics) strongly correlates with attrition.

* High OverTime pushes attrition risk sharply up — top feature in every model.

* Employees with short tenure or fewer promotions (FastPromoted = 0) are more likely to leave.

### 2. Behavioral & Demographic Patterns
* Younger employees (esp. under 35) show significantly higher attrition.

* Sales Representatives, Lab Technicians, and HR roles face higher churn.

* Employees with low monthly income and no recent promotion are more at risk.

* Frequent business travelers (especially young + traveling) tend to leave more.

### 3. Job Satisfaction Interactions
* SHAP dependence plots reveal that even high-paying roles can't retain employees with low job satisfaction.

* Conversely, lower-paid but satisfied employees tend to stay longer.


## Recommendations
### 1. Targeted Retention Strategy
* Focus efforts on Sales, Lab Techs, and HR roles.
* Provide career growth paths and regular engagement reviews.

### 2. Reduce OverTime
* Identify and reallocate workloads for employees with sustained overtime hours.
* Promote work-life balance — especially in tech and support functions.

### 3. Early Tenure Engagement
* Attrition spikes during the first 2 years — improve onboarding, mentorship, and early recognition programs.

### 4. Performance-Linked Growth
* Attrition is lower among those recently promoted.
* Consider “mini-promotions” or internal mobility every 12–18 months.

### 5. Compensation Review
* Attrition is high in “Very Low” and “Low” Income Buckets.
* Benchmark compensation in critical roles; offer skill-based bonus structure.

### 6. Manager Loyalty Index
* Higher LoyaltyIndex (Years with Manager / Years at Company) = lower attrition.
* Encourage manager continuity and skip-level feedback to improve retention.
