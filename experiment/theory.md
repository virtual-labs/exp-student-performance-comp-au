Predicting student performance from study hours is a classic regression task. This experiment compares three widely used regression techniques — **Linear Regression**, **Lasso Regression**, and **Ridge Regression** — to assess their predictive accuracy, stability, and generalization performance on noisy or high-dimensional data. Regularization methods such as Lasso and Ridge are specifically designed to prevent overfitting and enhance model robustness.

#### 1. Linear Regression (Ordinary Least Squares)

Linear Regression models the relationship between study hours (X) and exam score (Y) using a linear equation:

**`Y = β₀ + β₁ X + ε`**

Where:  
- Y → Exam score (dependent variable)  
- X → Number of study hours (independent variable)  
- β₀ → Intercept (expected score when X = 0)  
- β₁ → Slope (increase in score per extra hour)  
- ε → Random error, assumed ε ~ N(0, σ²)

**Interpretation Example**:  
A fitted model **`Ŷ = 40 + 5X`** means each additional study hour increases the predicted score by 5 points.

**Cost Function** (minimized by OLS):

**`J(β₀, β₁) = (1/n) Σ(i=1 to n) (Y_i − Ŷ_i)²`**

**Key Assumptions**:  
- Linearity  
- Independence  
- Homoscedasticity  
- Normality of residuals

#### 2. Lasso Regression (L1 Regularization)

Lasso adds an **L1 penalty** penalty to the cost function:

**`J(β₀, β) = MSE + α Σ(j=1 to p) |βⱼ|`**

**Key Characteristics**:  
- Drives unimportant coefficients **exactly to zero**  
- Performs **automatic feature selection**  
- Produces **sparse and interpretable** models

**Best for**: Student datasets with many predictors — Lasso will keep only the truly important ones (e.g., only study hours matter, sleep may be dropped).

#### 3. Ridge Regression (L2 Regularization)

Ridge adds an **L2 penalty** (squared coefficients):

**`J(β₀, β) = MSE + α Σ(j=1 to p) βⱼ²`**

**Key Characteristics**:  
- Shrinks coefficients toward zero but **rarely to exactly zero**  
- Excellent at handling **multicollinearity**  
- More stable when predictors are highly correlated

**Best for**: Cases where study hours, attendance, and revision time are correlated — Ridge keeps all but prevents extreme values.

#### Comparison of the Three Models

| Aspect                     | Linear Regression         | Lasso Regression                  | Ridge Regression                  |
|----------------------------|---------------------------|-----------------------------------|-----------------------------------|
| Regularization             | None                      | L1 → **`Σ |βⱼ|`**                | L2 → **`Σ βⱼ²`**                 |
| Feature Selection          | No                        | Yes (sets some β = 0)             | No                                |
| Handles Multicollinearity  | Poor                      | Moderate                          | Excellent                         |
| Coefficient Shrinkage      | None                      | Strong (can be zero)              | Moderate (near zero)              |
| Resulting Model            | Dense                     | Sparse                            | Dense                             |
| Best Use Case              | Clean, low-dim data       | Need sparsity & selection          | Correlated predictors              |


