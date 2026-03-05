# Adult-Income-Prediction
Machine Learning Project

Objective:
To apply the complete machine learning pipeline from data preprocessing to model building

1. CONCISE EXPLANATION
Summary of the Dataset
The Adult Income dataset, sourced from the UCI Machine Learning Repository, contains
demographic and employment-related data to predict whether a person earns more than $50K
per year. This is a binary classification problem.
 Target variable: income (<=50K or >50K)
 Features: 14 input features (a mix of numerical and categorical)
 Total instances: ~32,430 rows (after cleaning)
 Goal: Predict high-income individuals based on characteristics like age, education,
occupation, and hours worked per week.

Key EDA (Exploratory Data Analysis) Insights
 Age and hours-per-week are right-skewed; older individuals often work more and
are more likely to earn above $50K.
 Higher education levels (Bachelor’s, Master’s, Doctorate) are associated with higher
income.
 Capital gain/loss values are sparse; a large number of entries are zeros, indicating
most people did not report capital income.

 Males and married individuals show a significantly higher likelihood of earning above
$50K.
 Several categorical features like workclass, occupation, and native.country
contain ambiguous or missing entries, represented by the symbol "?".

Preprocessing Steps
1. Handling Missing Values:
o Rows with "?" in workclass, occupation, and native.country were
removed. These columns had overlapping missing data.
o native.country had the highest missing percentage and was dropped where
necessary.
2. Feature Encoding:
o Label Encoding was used for binary features such as sex and income, since
they have only two categories and do not require one-hot expansion.
o One-Hot Encoding was applied to nominal categorical features like
education, marital.status, occupation, etc., to avoid introducing any
artificial ordinal relationships.

3. Feature Scaling:
o Continuous numerical features such as age, hours-per-week, capital.gain,
and capital.loss were scaled using StandardScaler.
o Scaling ensures all numerical features contribute equally to the model
performance, especially important for distance-based algorithms.

4. Data Splitting:
o The dataset was split into:
 Training Set: 80% of the data (25,944 rows)
 Testing Set: 20% of the data (6,486 rows)
o A random_state was fixed to ensure reproducibility.

Modeling Approach
Several models were tested to evaluate performance:
 Logistic Regression:
o Served as a baseline linear model.
o Achieved ~78–80% accuracy.
o Simple and interpretable but less effective with nonlinear patterns.
 Decision Tree Classifier:
o Able to model non-linear relationships and interactions between features.
o Provided better accuracy than logistic regression but was prone to overfitting.
 Random Forest Classifier (Final Model):
o Achieved the highest accuracy, around 85.9%.
o Benefits from ensemble learning by combining multiple decision trees to
reduce overfitting and improve generalization.

o Automatically handles both categorical (after encoding) and numerical
features effectively.
o Was selected as the final model due to its superior performance, robustness,
and low bias.

Evaluation Metrics and Results
 Accuracy (Random Forest): ~85.9% on the test set.
 Confusion Matrix:
o Demonstrated a good balance between true positives and true negatives.
o Few misclassifications, indicating strong performance on both income
categories.

 Top Contributing Features:
o education, marital.status, occupation, hours-per-week, and
capital.gain were the most influential in determining income.

Classification Evaluation
The model's performance was assessed using a classification report, which included
precision, recall, and F1-score. It showed strong accuracy for both income classes, with
especially high performance on the majority class (<=50K). A confusion matrix heatmap was
also used to visualize prediction errors and confirmed the model’s effectiveness.

Conclusion
The Adult Income dataset presents a well-structured classification problem that benefits
greatly from proper data cleaning, encoding, and scaling. Among the models tested, the
Random Forest Classifier yielded the best performance in terms of accuracy and
generalization.
Key Takeaways:
 Tree-based ensemble methods are highly effective for structured tabular data.
 Feature encoding and handling of missing data are critical for robust performance.
 Income can be predicted with high reliability using demographic and occupational
attributes.
This project provides a strong foundation for predictive modeling on socio-economic datasets
and can be extended with hyperparameter tuning or feature selection for further
improvement.
