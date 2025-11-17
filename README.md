Causal Inference Project – Doubly Robust Estimation (DR)

This project estimates the Average Treatment Effect (ATE) of a binary treatment using observational data.
The analysis follows the Cultus requirements and includes:

✓ Data preprocessing

✓ Two Propensity Score Models

✓ Doubly Robust (DR) Estimator

✓ Sensitivity Analysis

✓ Final Interpretation & Insights


---

1. Project Overview

Estimating causal effects from observational data is challenging due to confounding variables.
To address this, the project combines:

Propensity Score Modeling

Outcome Regression Models

Doubly Robust Estimation (DR)

Sensitivity Checks


The DR estimator is highly reliable because it remains consistent if either the propensity score model or the outcome model is correctly specified.


---

2. Data Preprocessing

Steps performed:

1. Loaded dataset: causal_inference_dataset.csv


2. Handled missing values


3. Encoded categorical variables


4. Scaled numerical variables


5. Removed outliers where necessary


6. Selected confounders based on domain understanding (e.g., income, age, gender, prior purchases)


7. Split the data into Training & Testing sets



This ensures clean and consistent data for unbiased causal estimation.


---

3. Propensity Score Modeling

Two models were implemented:

Model 1 – Logistic Regression

Predicts probability of receiving treatment

Interpretable baseline model


Model 2 – Gradient Boosting Classifier (XGBoost or similar)

Non-linear, more flexible

Captures complex treatment assignment patterns


Outputs Stored:

Predicted propensity scores

Comparison of both models

Plots assessing overlap & balance (if applicable)



---

4. Doubly Robust (DR) Estimator

The DR estimator combines:

Outcome Model: Predicts expected outcome for treated vs control

Propensity Score: Adjusts for selection bias


Formula applied:

\hat{\tau}_{DR} = \frac{1}{n} \sum_{i=1}^{n} \left[ \frac{T_i(Y_i - \hat{m}_1(X_i))}{\hat{e}(X_i)} - \frac{(1-T_i)(Y_i - \hat{m}_0(X_i))}{1-\hat{e}(X_i)} + \hat{m}_1(X_i) - \hat{m}_0(X_i) \right]

Where:

 = Treatment (0/1)

 = Outcome

 = predicted propensity score

, = predicted outcomes


Output File

ate_results.csv contains:

ATE

Standard Error

95% Confidence Interval

Model comparison



---

5. Sensitivity Analysis

To check robustness:

1. Changed propensity score models


2. Modified outcome regression models


3. Tested model stability across multiple specifications


4. Examined if confounders had strong influence



This helps check whether the ATE remains stable under different assumptions.


---

6. Final Interpretation of Results

Summary of Findings (example wording based on your output):

The ATE was positive, indicating the treatment increases the outcome on average.

Confidence interval did not include zero → effect is statistically significant.

Both propensity score models produced similar ATE, suggesting stable estimation.

The DR estimator improved reliability by correcting model bias.


Key Insight

The treatment appears to have a consistent beneficial effect on the outcome across modeling strategies.


---

7. Repository Structure

📂 causal-inference/
│── README.md
│── causal_inference.ipynb
│── causal_inference_dataset.csv
│── ate_results.csv
│── preprocessor.joblib (optional)


---

8. How to Run the Notebook

1. Open causal_inference.ipynb in Jupyter/Colab


2. Upload the dataset


3. Run preprocessing


4. Run both propensity score models


5. Run the DR estimator


6. View ATE results

