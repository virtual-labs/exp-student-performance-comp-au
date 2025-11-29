

Predicting student performance from study hours is a classic regression task. This experiment compares three widely used regression techniques — **Linear Regression**, **Lasso Regression**, and **Ridge Regression** — to assess their predictive accuracy, stability, and generalization performance on noisy or high-dimensional data. Regularization methods such as Lasso and Ridge are specifically designed to prevent overfitting and enhance model robustness.

#### 1. Linear Regression (Ordinary Least Squares)

Linear Regression models the relationship between study hours (\(X\)) and exam score (\(Y\)) using a linear equation:

$$
Y = \beta_0 + \beta_1 X + \varepsilon
$$

Where:  
- \(Y\): Exam score (dependent variable)  
- \(X\): Number of study hours (independent variable)  
- \(\beta_0\): Intercept (expected score when \(X = 0\))  
- \(\beta_1\): Slope (change in score per additional study hour)  
- \(\varepsilon\): Random error term, assumed \(\varepsilon \sim N(0, \sigma^2)\)

**Interpretation Example**:  
A fitted model \(\hat{Y} = 40 + 5X\) indicates that each additional study hour increases the predicted score by 5 points.

**Cost Function** (minimized via Ordinary Least Squares):  
$$
J(\beta_0, \beta_1) = \frac{1}{n} \sum_{i=1}^{n} (Y_i - \hat{Y}_i)^2 \quad \text{(Mean Squared Error)}
$$

**Key Assumptions**:  
- Linearity between predictor and response  
- Independence of observations  
- Homoscedasticity (constant variance of residuals)  
- Normality of residuals (for valid inference)

#### 2. Lasso Regression (L1 Regularization)

Lasso (Least Absolute Shrinkage and Selection Operator) extends Linear Regression by adding an **L1 penalty**:

$$
J(\beta_0, \beta) = \text{MSE} + \alpha \sum_{j=1}^{p} |\beta_j|
$$

**Key Characteristics**:  
- The absolute value penalty drives less important coefficients **exactly to zero**  
- Enables **automatic feature selection**  
- Produces **sparse**, highly interpretable models  

**Practical Advantage in Student Data**:  
When multiple predictors (e.g., study hours, sleep duration, attendance) are included, Lasso eliminates irrelevant features, retaining only the most influential ones.

#### 3. Ridge Regression (L2 Regularization)

Ridge Regression incorporates an **L2 penalty** on the squared coefficients:

$$
J(\beta_0, \beta) = \text{MSE} + \alpha \sum_{j=1}^{p} \beta_j^2
$$

**Key Characteristics**:  
- Shrinks all coefficients toward zero but **rarely to exactly zero**  
- Highly effective against **multicollinearity**  
- Distributes coefficient influence more evenly  

**Practical Advantage in Student Data**:  
When predictors such as study hours, attendance, and revision time are correlated, Ridge prevents excessively large coefficients and yields a more stable model.

#### Comparison of the Three Models

| Aspect                     | Linear Regression         | Lasso Regression              | Ridge Regression              |
|----------------------------|---------------------------|-------------------------------|-------------------------------|
| Regularization             | None                      | L1 (\(\sum |\beta_j|\))       | L2 (\(\sum \beta_j^2\))       |
| Feature Selection          | No                        | Yes (sets some \(\beta = 0\)) | No                            |
| Handles Multicollinearity  | Poor                      | Moderate                      | Excellent                     |
| Coefficient Shrinkage      | None                      | Strong (can reach zero)       | Moderate (approaches zero)    |
| Resulting Model            | Dense                     | Sparse                        | Dense                         |
| Best Use Case              | Clean, low-dimensional data | Need for sparsity & selection | Correlated predictors         |
