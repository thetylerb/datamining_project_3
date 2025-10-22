# **Predicting House Prices with Regression**  
*A Data Mining Project by Tyler Buck*  

---

## **Project Overview**  
This project focused on predicting home sale prices using data from the Kaggle competition **House Prices: Advanced Regression Techniques**.  
The goal was to use regression models to estimate prices based on property characteristics such as living area, quality ratings, and year built.  
I started with a simple linear regression baseline and moved step by step toward more advanced models. Each stage focused on improving preprocessing, feature engineering, and algorithm performance.

---

## **Why Regression**  
Regression models are designed to predict a continuous value using one or more input variables.  
In this project, the target variable was `SalePrice`, and the predictors included both numerical and categorical features.  

A linear regression model tries to fit a straight line to the data using the equation:

`ŷ = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ + ε`



This assumes that each feature affects the price in a linear way.  
Because housing data often includes non-linear relationships, I later experimented with **Ridge**, **Lasso**, and **Gradient Boosting** models to capture more complex patterns.

---

## **Exploring the Data**  
Before building models, I explored and visualized the dataset to understand relationships between variables.  
I looked at missing values, feature distributions, and correlations between variables.  
The strongest predictors of price were **Overall Quality**, **Living Area**, and **Total Basement Square Footage**.  
Homes with higher quality ratings and larger sizes tended to sell for more, while older homes or those without renovations were generally valued lower.

---

## **Preprocessing and Feature Engineering**  
Cleaning and transforming the data was a key step.  
I filled missing numerical values with median values and categorical variables with their most frequent entries.  
Then I created new features to capture additional structure:  

- `TotalSF` = sum of above-ground living area and basement area  
- `HouseAge` = years since construction  
- `TotalBaths` = combined number of full and half bathrooms  
- `QualityScore` = combined measure of overall, kitchen, and exterior quality  

I converted categorical variables to numerical form using one-hot encoding.  
These new features helped the models learn relationships that were not obvious from the raw data.

---

## **Experiment 1: Linear Regression**  
The baseline model was a simple linear regression.  
It achieved an RMSE of about **45,900** and an R² of **0.73**.  
The model explained most of the price variance but performed poorly for high-value properties where relationships were not linear.

---

## **Experiment 2: Ridge and Lasso Regression**  
To reduce overfitting and stabilize coefficients, I applied **Ridge (L2)** and **Lasso (L1)** regression.  
After tuning the regularization parameter α, Ridge achieved the best performance with an RMSE of **45,900 ± 17,300**, while Lasso performed worse.  
Ridge offered a small but consistent improvement and became the preferred linear model.

---

## **Experiment 3: Gradient Boosting**  
Next, I used a **HistGradientBoostingRegressor**, which combines many decision trees to model non-linear relationships.  
After tuning hyperparameters such as learning rate, tree depth, and regularization, the model achieved an average **RMSE of 10,262 ± 3,867**.  
This was a large improvement over linear methods and showed that tree-based models handle complex housing data more effectively.  
The model learned interactions between features such as size, age, and quality that linear regression could not capture.

---

## **Ethical and Practical Impact**  
Predicting home prices can support fair market analysis and appraisal, but there are important considerations.  
Housing data can reflect social and geographic inequalities.  
Models built from historical data should be used carefully to avoid reinforcing bias or creating unfair assessments.  
Transparency and fairness should always guide the deployment of predictive models in real estate.

---

## **Lessons Learned**  
Through this project I learned that:  
1. Starting simple helps establish a reliable baseline before adding complexity.  
2. Feature engineering often provides bigger gains than switching algorithms.  
3. Regularization improves model stability without large accuracy losses.  
4. Tree-based models are best for capturing non-linear and interaction effects.  
5. Cross-validation and RMSE provide consistent ways to compare models.

---

## **Tools Used**  
- **Python**, **pandas**, **NumPy**, **matplotlib**, **seaborn**  
- **scikit-learn:** LinearRegression, Ridge, Lasso, HistGradientBoostingRegressor  
- **Evaluation metrics:** RMSE, cross-validation  

---

## **Project Files**  


Project Files
dm_project_3/
├── dm_project_3_starter.ipynb   # Full notebook
├── data_description.txt         # Dataset information
├── submission.csv               # Optional Kaggle submission
├── README.md                    # Project summary
└── .gitignore                   # Cleanup file


---

## **Key Takeaways**  
- Iterative modeling led to steady performance improvement from linear to ensemble methods.  
- Thoughtful feature engineering had the largest effect on accuracy.  
- Ridge regularization provided a strong, stable linear baseline.  
- Gradient Boosting captured complex relationships and achieved the best RMSE (~10k).  
- Responsible use of housing data requires awareness of bias, transparency, and fairness.  
