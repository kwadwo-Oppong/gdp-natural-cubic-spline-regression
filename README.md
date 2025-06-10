# GDP Analysis with Natural Cubic Splines and ElasticNet Regression
An econometric analysis of the Acemoglu, Johnson, and Robinson dataset, exploring factors influencing GDP using statistical modeling, advanced feature engineering with natural cubic splines, and a comparison of Ordinary Least Squares (OLS) with a robust **ElasticNet** regression

## Project Overview
This project delves into the determinants of economic prosperity using the historical `acemoglu_johnson_robinson.txt` dataset. The primary goal is to model the relationship between GDP and various socio-economic and geographical factors. We start with fundamental data analysis techniques, including descriptive statistics and data preprocessing. A key aspect of this project involves `feature engineering` using natural cubic splines to capture non-linear relationships, specifically with Latitude. The analysis progresses from estimating a baseline linear model with **Ordinary Least Squares (OLS)**, assessing its strengths and weaknesses, to proposing and implementing ElasticNet regression as a more suitable estimator to address potential limitations inherent in the OLS approach for this dataset.

## Key Features & Techniques
- **Data Loading & Initial Exploration**: Loading the `acemoglu_johnson_robinson.txt` dataset into a pandas DataFrame.
- **Descriptive Statistics**: Generating summary statistics and scatterplots for continuous variables.
- **Data Preprocessing**:
  - Centering the **GDP** variable.
  - Standardizing all other continuous variables (mean zero, variance one).
- **Feature Engineering with Natural Cubic Splines**:
  - Implementing a custom `NaturalCubicSpline` class to create a natural cubic spline basis for **Latitude** with 20 evenly spaced knots.
  - Constructing a comprehensive predictor matrix `X` that includes all processed variables and the generated spline basis.
- **Ordinary Least Squares (OLS) Regression**:
  - Estimating the linear relationship between the transformed GDP and the engineered predictor matrix `X` using `statsmodels`.
  - Reporting coefficients and discussing the merits and limitations of OLS in this context.
- **Advanced Estimator Implementation (ElasticNet)**:
  - Implementing **ElasticNet** regression using `sklearn.linear_model` to address issues like overfitting and multicollinearity observed with OLS.
  - Reporting and comparing coefficients and findings from the ElasticNet model.

## Dataset
The project utilizes the `acemoglu_johnson_robinson.txt` dataset, a tabular dataset containing various socio-economic and geographical indicators for different countries. The primary target variable is **GDP**, and other variables include Latitude, among others, which are used as predictors.

## Results & Discussion
The analysis demonstrates how data transformations and feature engineering, particularly with natural cubic splines, can enhance predictive power by capturing non-linear relationships. The OLS model provides a baseline understanding of variable relationships.

To address the limitations of OLS, such as overfitting and multicollinearity, **ElasticNet** regression was implemented. The coefficients from the ElasticNet model are notably smaller compared to OLS coefficients for the same variables, which indicates a successful correction for overfitting through regularization. ElasticNet also effectively handles multicollinearity by combining the strengths of Ridge and Lasso penalties, making it suitable for high-dimensional datasets where feature selection is crucial while retaining correlated predictors.

