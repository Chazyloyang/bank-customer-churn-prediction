# Bank Customer Churn Prediction System

## Project Overview
This project aims to develop a robust system for predicting bank customer churn. By leveraging machine learning techniques, we identify customers at risk of churning, analyze the key factors contributing to churn, and provide actionable business recommendations to enhance customer retention efforts.

## Dataset
The project utilizes a publicly available bank customer churn dataset (`Churn_Modelling.csv`).

**Key Features:**
*   `CreditScore`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`
*   Categorical features: `Geography`, `Gender`
*   Target variable: `Exited` (1 = Churned, 0 = Not Churned)

## Methodology
The project followed a structured machine learning pipeline:

1.  **Data Loading & Initial Exploration:** Loaded the dataset and performed initial checks (`df.info()`, `df.describe()`).
2.  **Data Cleaning & Preprocessing:** Dropped irrelevant columns (`RowNumber`, `CustomerId`, `Surname`).
3.  **Exploratory Data Analysis (EDA):** Visualized distributions of the target variable and features. Key insights included class imbalance, higher churn in Germany, slightly higher churn for females, increased churn risk for older customers (40-60), and lower churn for customers with zero balance.
4.  **Feature Engineering & Encoding:** One-hot encoded categorical features (`Geography`, `Gender`). Scaled numerical features using `StandardScaler` after splitting the data into training and testing sets.
5.  **Model Training & Comparison:** Trained and evaluated three classification models:
    *   **Logistic Regression**
    *   **Random Forest Classifier**
    *   **XGBoost Classifier**

    Models were evaluated using Accuracy, Precision, Recall, F1-Score, and ROC-AUC. XGBoost emerged as the best model, particularly due to its high Recall (61.92%) and strong F1-Score (58.67%) and ROC-AUC (83.58%), which are crucial for identifying potential churners.
6.  **Feature Importance Analysis:** Analyzed XGBoost feature importances, identifying `NumOfProducts`, `IsActiveMember`, `Age`, `Geography_Germany`, and `Balance` as the most influential factors.
7.  **Churn Probability Scoring System:** Developed a system to categorize customers into 'Low Risk', 'Medium Risk', and 'High Risk' based on their churn probabilities predicted by the XGBoost model.

## Key Findings
*   **Class Imbalance:** The dataset shows a significant imbalance between churned and non-churned customers.
*   **Geographical Impact:** Germany exhibited a higher churn rate compared to other regions.
*   **Demographic Factors:** Older customers (40-60 years) and females showed a slightly higher propensity to churn.
*   **Behavioral Indicators:** Customers with fewer products and those who are inactive members are more likely to churn. Customers with zero balance are less likely to churn.
*   **Model Performance:** The XGBoost model demonstrated superior performance in identifying churners, with a good balance of precision and recall.

## Business Recommendations
Based on the analysis, the following recommendations are made:

### 1. Targeted Retention Campaigns
*   **High-Risk Customers:** Engage immediately with personalized offers (e.g., fee waivers, premium services, dedicated support).
*   **Medium-Risk Customers:** Implement proactive outreach (e.g., loyalty programs, financial health check-ups, satisfaction surveys).
*   **Low-Risk Customers:** Maintain regular, less intensive engagement (e.g., newsletters, special offers).

### 2. Product Offering and Engagement Strategies
*   **Address 'NumOfProducts' Impact:** Investigate why customers with fewer products churn. Offer incentives for cross-selling relevant products to increase engagement. Conversely, investigate if high `NumOfProducts` is causing issues.
*   **Encourage Active Membership:** Implement gamification, rewards for digital service usage, or personalized financial tips to boost `IsActiveMember` status.

### 3. Demographic and Behavioral Segment-Specific Actions
*   **Age-Specific Interventions:** Tailor offers for older customers (e.g., retirement planning, traditional services).
*   **Geographical Focus:** Investigate and address specific churn drivers in high-churn regions like Germany with localized strategies.
*   **Balance Management:** Offer financial planning tools and savings incentives to customers with low balances to increase their engagement.

### 4. Continuous Monitoring and Feedback Loop
*   **Regular Model Updates:** Periodically retrain the churn prediction model with new data to maintain its accuracy.
*   **Customer Feedback:** Establish channels for feedback, especially from at-risk customers, to understand and address their evolving needs.
