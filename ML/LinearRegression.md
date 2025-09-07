
### Linear Regression: Detailed Revision Notes

Linear Regression is a fundamental **supervised learning model** used in machine learning and statistics. It falls under the category of **regression models** within supervised learning because its **target variable is continuous in nature**.

**1. Definition and Purpose**
*   Linear Regression is a technique for **finding and modelling the relationship between two or more variables**.
*   The primary goal is to **predict a continuous target variable (dependent variable)** based on the values of one or more **independent variables (features)**.
*   It aims to **capture linear dependencies** in data, meaning as one variable increases/decreases, the other increases/decreases by a proportional amount.

**2. Core Concepts and Terminology**
*   **Dependent Variable (Target/Response/Y)**: The variable you want to predict.
    *   *Example:* Price of a house, a person's height, amount of spend by a customer.
*   **Independent Variable (Features/Predictor/X)**: The factors or attributes that influence the dependent variable.
    *   *Example:* Number of rooms, age of the house, location (for house price prediction).
*   **Linear Relationship**:
    *   **Direct (Positive) Relationship**: As the independent variable increases, the dependent variable also increases. The regression line will have a positive slope.
        *   *Examples:* Temperature vs. ice cream cones sold, student study hours vs. score, experience vs. salary.
    *   **Inverse (Negative) Relationship**: As the independent variable increases, the dependent variable decreases. The regression line will have a negative slope.
        *   *Examples:* Temperature vs. number of clothes worn, price vs. demand, crime rate vs. house price.
*   **Line of Best Fit (Regression Line)**:
    *   Linear regression seeks to find the straight line that best represents the relationship between the variables.
    *   This line minimises the **vertical distances (errors/residuals)** of all data points from itself, making it the line with the **minimum error**.
    *   The output of a linear regression model is the **equation of this straight line**: **Y = mX + C**.
        *   **Y**: Dependent variable (target).
        *   **X**: Independent variable (feature).
        *   **m**: **Slope (coefficient)**, indicating the change in Y for a one-unit change in X. A positive 'm' indicates a direct relationship, a negative 'm' indicates an inverse relationship.
        *   **C**: **Constant (intercept)**, representing the value of Y when X is zero.

**3. Mathematical Underpinnings (Internal Working)**
*   While users typically don't perform these manually in Python, the model calculates 'm' and 'C' using statistical formulas.
*   The line of best fit always **passes through the average of X and Y values**.
*   The objective is to **minimise the sum of squared errors** (vertical distances between actual data points and the predicted line) to determine the best 'm' and 'C'.

**4. Types of Linear Regression**
*   **Simple Linear Regression**: Involves **only one independent variable** to predict the target variable.
*   **Multiple Linear Regression**: Uses **more than one independent variable** to predict the target variable.

**5. Prerequisites and Assumptions**
*   **Programming Language**: Preferably Python, but knowledge of any programming language is acceptable.
*   **Mathematics**: Basic understanding of statistics, including mean, median, mode, standard deviation, and variance.
*   **Features must be correlated with the target variable**.
*   **Independent variables should NOT be highly correlated among themselves** (this is known as **multicollinearity**).
    *   **Variance Inflation Factor (VIF)**: A metric used to detect multicollinearity among independent variables. A high VIF value (e.g., >5 or >6) for a feature suggests it is highly correlated with other features, and its removal might be considered.

**6. Model Evaluation Metrics**
*   **R-squared (R²)**: Also known as the **"goodness of fit"**.
    *   Measures how well the independent variables explain the variation in the dependent variable.
    *   Ranges from **0 to 1**.
    *   A **higher R-squared value indicates a better model**.
    *   **Interpretation**: An R-squared of 0.8 means the model captures 80% of the variation in the target variable using the given features.
    *   **Good R-squared**: Generally, an R-squared **greater than 0.7 (70%)** is considered good, but this can vary by domain. A lower value suggests a need for more relevant features.
*   **Mean Absolute Error (MAE)**: The average of the absolute differences between predicted and actual values.
*   **Mean Squared Error (MSE)**: The average of the squared differences between predicted and actual values. It penalises larger errors more heavily.
*   **Root Mean Squared Error (RMSE)**: The square root of MSE, bringing the error back to the original units of the target variable.
*   **Mean Absolute Percentage Error (MAPE)**: Measures the average percentage error of the predictions.

**7. Model Implementation Steps (General)**
1.  **Data Loading and Initial Exploration (EDA)**: Understand the data, check for types, distributions, and outliers.
2.  **Data Cleaning**: Handle missing values (e.g., imputation, dropping), duplicates, and potentially invalid values.
3.  **Feature Engineering**: Transform categorical variables into numerical ones (e.g., Label Encoding or One-Hot Encoding). (Note: For ordinal variables, Label Encoding may be suitable; for nominal, One-Hot Encoding is generally preferred to avoid introducing artificial order).
4.  **Feature Selection**: Identify relevant features and assess their correlation with the target variable.
5.  **Data Splitting**: Divide the data into **training** (e.g., 70-80%) and **testing** (e.g., 20-30%) sets. The training data is used to build the model, and the testing data evaluates its performance on unseen data. A `random_state` ensures reproducibility of the split.
6.  **Model Training (Fitting)**: Instantiate the `LinearRegression` model object and fit it to the training data (`X_train`, `y_train`).
7.  **Prediction**: Use the trained model to make predictions on the testing data (`X_test`).
8.  **Model Evaluation**: Compare predicted values (`y_pred`) with actual test values (`y_test`) using metrics like R-squared, MAE, MSE, RMSE, and MAPE.
9.  **Interpretation of Coefficients**: Understand how each feature impacts the target variable based on its coefficient.

**8. Relationship with Overfitting, Underfitting, and Bias-Variance Trade-off**
*   **Overfitting**: Occurs when a model learns the training data too well, including noise, and performs poorly on new data. Linear regression models can overfit if too many irrelevant or highly correlated features are included.
*   **Underfitting**: Occurs when a model is too simple and fails to capture the underlying patterns in the data, leading to poor performance on both training and new data. This can happen in linear regression if important features are missing or the relationship is non-linear.
*   **Good Fit**: The goal is to achieve a balance between underfitting and overfitting, where the model generalises well to unseen data.
*   **Bias-Variance Trade-off**: Represents the balance between two sources of error. High bias (underfitting) means the model is too simple; high variance (overfitting) means the model is too complex. The aim is to minimise both for optimal generalisation.
*   **Regularisation (L1/Lasso, L2/Ridge)**: Techniques applied to linear regression (and other models) to prevent overfitting by adding a penalty to the model's complexity during training. They can also help address multicollinearity.

**9. Distinction from Logistic Regression**
*   While both have "regression" in their names, **Linear Regression is for continuous target variables**, whereas **Logistic Regression is for categorical target variables (classification problems)**. Logistic regression outputs probabilities, typically in an S-shaped curve (sigmoid function), rather than a straight line.