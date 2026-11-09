# Practical Application III: Comparing Classifiers

**Overview**: This repository contains the code and analysis for Practical Application III, where the performance of four core classification algorithms—**K-Nearest Neighbors (KNN)**, **Logistic Regression**, **Decision Trees**, and **Support Vector Machines (SVM)**—is evaluated and compared. The project utilizes a real-world marketing dataset from a Portuguese banking institution focused on direct telephone marketing campaigns.

---

## 📋 Business Objective
The primary business objective is to predict whether a bank client will subscribe to a term deposit (`y` target variable) based on demographic, historical campaign, and socio-economic features. By accurately identifying prospective subscribers, the bank can optimize its marketing resources, improve campaign efficiency, and target outreach efforts toward high-probability customers.

---

## 📊 Dataset Description
The dataset originates from the UCI Machine Learning Repository (`bank-additional-full.csv`) and encompasses 41,188 records with 21 input features:

* **Bank Client Data**: `age`, `job`, `marital`, `education`, `default`, `housing`, `loan`
* **Last Contact Details**: `contact`, `month`, `day_of_week`, `duration` *(Note: As specified in the dataset documentation, `duration` is highly correlated with the target variable but is unknown before a call is made; therefore, it was dropped to build a realistic predictive model)*
* **Other Attributes**: `campaign`, `pdays`, `previous`, `poutcome`
* **Social & Economic Context**: `emp.var.rate`, `cons.price.idx`, `cons.conf.idx`, `euribor3m`, `nr.employed`
* **Target Variable**: `y` (Term deposit subscription: 'yes' or 'no')

---

## 🛠️ Methodology & Workflow
1. **Data Inspection & Cleaning**: Loaded the dataset using `pandas`, inspected data types and missing values, and successfully dropped the `duration` feature to prevent data leakage in predictive modeling.
2. **Exploratory Data Analysis (EDA)**: Analyzed feature distributions, class imbalances (term deposit subscriptions represent a minority class), and relationships between socio-economic indicators and customer behavior.
3. **Data Preprocessing**: Handled categorical variables (via encoding), scaled numerical features, and partitioned the data into training and testing sets.
4. **Model Training & Evaluation**: Trained and tuned the following classifiers:
   * **K-Nearest Neighbors (KNN)**
   * **Logistic Regression**
   * **Decision Trees**
   * **Support Vector Machines (SVM)**
5. **Performance Comparison**: Evaluated models using metrics appropriate for imbalanced classification (Accuracy, Precision, Recall, F1-Score, and ROC-AUC).

---

## 📈 Key Findings & Model Comparison

| Classifier | Strengths | Considerations / Performance Highlights |
| :--- | :--- | :--- |
| **Logistic Regression** | Highly interpretable, fast training time, provides baseline linear probabilities. | Performs well on linearly separable data but may struggle with complex non-linear feature interactions. |
| **Decision Trees** | Intuitive, handles non-linear relationships well, easy to visualize feature importance. | Prone to overfitting if tree depth is unconstrained. |
| **K-Nearest Neighbors** | Non-parametric, simple to implement for instance-based learning. | Computationally expensive on large datasets ($N = 41,188$) and sensitive to feature scaling. |
| **Support Vector Machines** | Effective in high-dimensional spaces, robust against overfitting with proper kernel selection. | High training complexity and sensitive to hyperparameter tuning (`C` and `gamma`). |

---

## 💡 Business Recommendations
* **Targeted Marketing Campaigns**: Focus future telephone campaigns on clients exhibiting high socio-economic stability indicators (e.g., favorable euribor rates and employment variation rates) and favorable previous campaign outcomes (`poutcome = success`).
* **Resource Optimization**: Avoid redundant calls to clients with high contact counts (`campaign`) who have historically shown no interest, thereby reducing operational costs.
* **Model Deployment**: Implement Logistic Regression or tuned Decision Trees for real-time lead scoring to assist marketing agents in prioritizing high-conversion prospects.

---

## ⚙️ Repository Structure
```text
├── data/
│   └── bank-additional-full.csv    # Dataset file
├── notebooks/                      # Jupyter notebooks with full analysis
├── README.md                       # Project documentation
