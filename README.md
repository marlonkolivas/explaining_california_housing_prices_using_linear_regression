## Explaining California Housing Prices Using Linear Regression

### Project Overview

This project builds an interpretable machine learning model to explain and predict housing prices across California districts using demographic and geographic census data.

The goal is not only prediction accuracy but also understanding the drivers of housing prices. For this reason, the project uses Linear Regression (Ordinary Least Squares) as a transparent baseline model.

Through exploratory data analysis, model training, and diagnostic evaluation, the project investigates which socioeconomic factors most strongly influence housing values.

### Dataset

The dataset used in this project is the California Housing dataset available through scikit-learn.

It contains aggregated information collected from the 1990 U.S. Census across California districts.

#### Features

| Feature     | Description                         |
|-------------|-------------------------------------|
| MedInc      | Median income of households         |
| HouseAge    | Median house age                    |
| AveRooms    | Average number of rooms             |
| AveBedrms   | Average number of bedrooms          |
| Population  | District population                 |
| AveOccup    | Average household occupancy         |
| Latitude    | Geographic latitude                 |
| Longitude   | Geographic longitude                |

### Target Variable

MedHouseVal
Median house value in the district (measured in $100,000 units).

### Project Workflow

**1. Data Loading** <br>
The California Housing dataset is loaded from scikit-learn and converted into a Pandas DataFrame for analysis.

**2. Data Audit**<br>
Initial inspection verifies:
- dataset shape
- column structure
- descriptive statistics
- missing values

The dataset contains no missing values, but several variables exhibit extreme outliers, especially population-related variables.

**3. Exploratory Data Analysis (EDA)** <br>
EDA was conducted to understand the data structure and relationships between variables.

Key analyses include:
- target variable distribution
- feature distributions
- correlation heatmap
- scatter plots of key predictors

Important observations:
- Median income shows the strongest relationship with housing prices.
- Several population-related variables exhibit heavy skew.
- Geographic features reveal regional price clustering.

**4. Baseline Model** <br>
Before training a machine learning model, a baseline model was created that simply predicts the mean house value.

Baseline results: <br>
MAE: 0.91
RMSE: 1.31
R²: ~0

This baseline provides a benchmark to determine whether the regression model meaningfully improves prediction performance.

**5. Linear Regression Model** <br>
A Linear Regression model was implemented using a Scikit-learn Pipeline including: <br>
- StandardScaler
- LinearRegression

Scaling was applied to improve numerical stability and allow coefficient interpretation.

**6. Model Evaluation** <br>
The dataset was split into training and testing sets to simulate real-world predictive performance.

Evaluation metrics:
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- R² (Coefficient of Determination)

Model results:<br>
| Metric | Baseline | Linear Regression |
|------|------|------|
| MAE | 0.91 | 0.53 |
| RMSE | 1.31 | 0.56 |
| R² | ~0 | ~0.64 |

**7. Cross-Validation** <br>
To ensure the model generalizes well, cross-validation was applied on the training set. <br>
Results confirmed that the model’s performance is stable across folds, indicating reliable predictive behavior.

**8. Model Interpretation**<br>

One advantage of linear regression is interpretability.

A standardized coefficient analysis reveals:
- Median Income is the strongest driver of housing prices.
- Geographic variables capture regional price differences.
- Housing characteristics such as average rooms and bedrooms also influence prices.


**9. Residual Diagnostics**<br>
Residual analysis helps verify the assumptions of linear regression.

Key observations:
- The model tends to underpredict low-value homes and overpredict very expensive homes.
- A ceiling effect exists in the dataset due to a capped maximum house value.
- Some districts contain unusual feature values that generate large prediction errors.


**10. Error Analysis**

Inspection of the largest prediction errors shows they are often associated with:
- extreme population values
- unusual housing characteristics
- capped high-price districts

This analysis highlights potential improvements such as:
- feature transformations
- regularized regression
- non-linear models


**Key Insights**

Several meaningful insights emerge from the analysis:
- Income is the dominant predictor of housing prices.
- Housing markets show strong regional clustering.
- Population-related variables introduce noise due to extreme values.
- A simple interpretable model can explain a significant portion of housing price variation.
