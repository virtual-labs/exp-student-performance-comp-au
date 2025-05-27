<h3>Theory</h3>

<p>
  Predicting student performance (e.g., exam scores) based on study hours is a regression problem that aims to model the relationship between an independent variable (study hours) and a dependent variable (performance). This study compares three regression models—Linear, Lasso, and Ridge—to evaluate their effectiveness in terms of prediction accuracy, robustness, and interpretability. Regularization techniques (Lasso and Ridge) help address challenges such as overfitting, noise, and potential multicollinearity in multi-feature scenarios.
</p>

<h4>Linear Regression</h4>
<p>
  Linear Regression models the relationship between study hours (<i>x</i>) and student performance (<i>y</i>) as a straight line:
</p>
<p><i>y = β<sub>0</sub> + β<sub>1</sub>x + ϵ</i></p>
<ul>
  <li><i>y</i>: Predicted performance (e.g., score out of 100).</li>
  <li><i>x</i>: Study hours (e.g., hours per day).</li>
  <li><i>β<sub>0</sub></i>: Intercept (baseline performance when study hours are 0).</li>
  <li><i>β<sub>1</sub></i>: Slope (increase in performance per additional study hour).</li>
  <li><i>ϵ</i>: Error term (captures unmodeled factors like stress or prior knowledge).</li>
</ul>

<h4>Objective</h4>
<p>The model minimizes the Mean Squared Error (MSE):</p>
<p>
  J(β<sub>0</sub>, β<sub>1</sub>) = 
  <sup>1</sup>/<sub>m</sub> &sum;<sub>i=1</sub><sup>m</sup> (y<sub>i</sub> - ŷ<sub>i</sub>)<sup>2</sup>
</p>
<p>
  where <i>m</i> is the number of students, <i>y<sub>i</sub></i> is the actual score, and 
  <i>ŷ<sub>i</sub> = β<sub>0</sub> + β<sub>1</sub>x<sub>i</sub></i> is the predicted score. 
  The optimal β<sub>0</sub> and β<sub>1</sub> are found using Ordinary Least Squares (OLS).
</p>

<h4>Assumptions</h4>
<ul>
  <li>The relationship between study hours and performance is linear.</li>
  <li>Errors (ϵ) are normally distributed with constant variance (homoscedasticity).</li>
  <li>Observations are independent (one student’s performance does not influence another’s).</li>
</ul>

<h4>Practical Implications</h4>
<p>
  Linear Regression is simple and interpretable: β<sub>1</sub> directly indicates how much performance improves per study hour. However, it may overfit if the dataset is small or noisy, and it’s sensitive to outliers (e.g., a student who studies 10 hours but scores poorly due to external factors).
</p>

<h4>Lasso Regression (L1 Regularization)</h4>

<h4>Concept</h4>
<p>
  Lasso Regression adds an L1 penalty to the Linear Regression cost function:
</p>
<p>
  <i>J(β<sub>0</sub>, β<sub>1</sub>) = (1/m) Σ(y<sub>i</sub> - ŷ<sub>i</sub>)² + α |β<sub>1</sub>|</i>
</p>
<ul>
  <li><i>α</i>: Regularization parameter (controls penalty strength).</li>
  <li><i>|β<sub>1</sub>|</i>: Absolute value of the coefficient.</li>
</ul>

<h4>Mechanism</h4>
<p>
  The L1 penalty encourages sparsity by shrinking β<sub>1</sub> to zero if study hours are deemed irrelevant. While this effect is limited in single-variable models, Lasso becomes powerful in multi-feature scenarios (e.g., including sleep hours, attendance) as it can eliminate less important variables.
</p>

<h4>Benefits</h4>
<ul>
  <li><b>Feature Selection:</b> Sets coefficients to zero, simplifying the model.</li>
  <li><b>Overfitting Prevention:</b> Shrinks coefficients to reduce sensitivity to noise.</li>
  <li><b>Interpretability:</b> Emphasizes the most impactful predictors.</li>
</ul>

<h4>Practical Implications</h4>
<p>
  For predicting student performance, Lasso helps prevent overfitting to noisy data (e.g., a student who studies little but scores high due to prior knowledge). The α parameter allows tuning: a small α (e.g., 0.1) applies light regularization, while a large α (e.g., 5.0) may overly simplify the model.
</p>

<h4>Ridge Regression (L2 Regularization)</h4>

<h4>Concept</h4>
<p>
  Ridge Regression introduces an L2 penalty to the Linear Regression cost function:
</p>
<p>
  <i>J(β<sub>0</sub>, β<sub>1</sub>) = (1/m) Σ(y<sub>i</sub> - ŷ<sub>i</sub>)² + α β<sub>1</sub><sup>2</sup></i>
</p>
<ul>
  <li><i>α</i>: Regularization parameter controlling the strength of the penalty.</li>
  <li><i>β<sub>1</sub><sup>2</sup></i>: Squared value of the coefficient (L2 norm).</li>
</ul>

<h4>Mechanism</h4>
<p>
  The L2 penalty reduces the magnitude of coefficients but does not set them to zero. It distributes the effect across all features, making it more suitable when all features contribute to prediction.
</p>

<h4>Benefits</h4>
<ul>
  <li><b>Stability:</b> Handles multicollinearity by reducing the impact of correlated features.</li>
  <li><b>Improved Generalization:</b> Prevents overfitting in high-variance datasets.</li>
  <li><b>Robustness:</b> Performs well even when many features are weak but useful together.</li>
</ul>

<h4>Practical Implications</h4>
<p>
  In the context of predicting student performance, Ridge Regression is useful when several factors (e.g., study hours, attendance, sleep, stress) collectively influence performance. It offers better stability in model estimates when all features are moderately predictive.
</p>
