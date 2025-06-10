# GDP Analysis with Natural Cubic Splines and ElasticNet Regression
An econometric analysis of the Acemoglu, Johnson, and Robinson dataset, exploring factors influencing GDP using statistical modeling, advanced feature engineering with natural cubic splines, and a comparison of Ordinary Least Squares (OLS) with a robust **ElasticNet** regression

## Table of Contents
* [Project Overview](#project-overview)
* [Key Features & Techniques](#key-features--techniques)
* [Dataset](#dataset)
* [Project Structure](#project-structure)
* [How to Run](#how-to-run)
* [Dependencies](#dependencies)
* [Results & Discussion](#results--discussion)
* [Limitations & Future Work](#limitations--future-work)
* [Contact](#contact)
* [License](#license)

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



## Project Structure
```
.
├── acemoglu_johnson_robinson.txt  # The input dataset
├── CORRECT_COURSEWORK.ipynb       # Jupyter Notebook containing all the code and analysis
└── README.md                      # This README file
```
## How to run
To run this project locally, follow these steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/[Your-GitHub-Username]/[your-repository-name].git
   cd [your-repository-name]

2. Create a virtual environment (recommended):
  ```bash
  python -m venv venv
  source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

3. Install dependencies:
```bash
  pip install -r requirements.txt
```
(If you don't have a `requirements.txt` yet, create one by running `pip freeze > requirements.txt` after installing all dependencies, or install them manually as listed below.)

4. Run the analysis:
   - Open and run the Jupyer Notebook
   ```Code snippet
   jupyter notebook name.ipynb
   ```
  Then open the notebook in your browser and execute the cells sequentially.

## Dependencies
This project relies on the following Python libraries:
- **pandas**: For data manipulation and analysis.
- **numpy**: For numerical operations.
- **matplotlib**: For plotting and visualizations.
- **seaborn**: For enhanced statistical data visualization.
- **scikit-learn**: For data preprocessing (StandardScaler) and advanced linear models (Lasso, ElasticNet).
- **statsmodels**: For Ordinary Least Squares (OLS) regression.

You can install them using pip:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels
```

## Results & Discussion
The analysis demonstrates how data transformations and feature engineering, particularly with natural cubic splines, can enhance predictive power by capturing non-linear relationships. The OLS model provides a baseline understanding of variable relationships.

To address the limitations of OLS, such as overfitting and multicollinearity, **ElasticNet** regression was implemented. The coefficients from the ElasticNet model are notably smaller compared to OLS coefficients for the same variables, which indicates a successful correction for overfitting through regularization. ElasticNet also effectively handles multicollinearity by combining the strengths of Ridge and Lasso penalties, making it suitable for high-dimensional datasets where feature selection is crucial while retaining correlated predictors.

## Limitations & Future Work
While this project addresses several aspects of economic data analysis, potential limitations include:
- The specific choice of 20 knots for the natural cubic spline is based on intuition and could be further optimized using data-driven methods.
- The `acemoglu_johnson_robinson.txt` dataset's scope may limit the generalizability of findings to other contexts or time periods.


Future work could involve:
- Cross-validation to determine the optimal number of knots for the splines.
- Exploring other non-linear modeling techniques or more advanced regularization methods.
- Conducting robustness checks by applying the analysis to different economic datasets.
- A deeper dive into the interpretation of spline coefficients and their implications for the relationship between Latitude and GDP.

## Contact
Feel free to reach out if you have any questions or feedback!

## License
This project is licensed under the MIT License - see the [LICENSE](#license) file for details.

