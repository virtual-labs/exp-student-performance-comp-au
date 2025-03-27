<h3>Theory</h3>

<p>Predicting student performance (e.g., exam scores) based on study hours is a regression problem aimed at modeling the relationship between an independent variable (study hours) and a dependent variable (performance). This study compares three regression models—Linear, Lasso, and Ridge—to evaluate their effectiveness in terms of prediction accuracy, robustness, and interpretability. Regularization techniques (Lasso and Ridge) are used to address challenges like overfitting, noise, and potential multicollinearity in future multi-feature scenarios.</p>
<h4>Linear Regression</h4>
<p>Linear Regression models the relationship between study hours (<i>x</i>) and student performance (<i>y</i>) as a straight line:</p>
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

<h4> Assumptions</h4>
<ul>
  <li>The relationship between study hours and performance is linear.</li>
  <li>Errors (ε) are normally distributed with constant variance (homoscedasticity).</li>
  <li>Observations are independent (one student’s performance doesn’t affect another’s).</li>
</ul>

<h4> Practical Implications</h4>
<p>
  Linear Regression is simple and interpretable: β<sub>1</sub> directly indicates how much 
  performance improves per study hour. However, it may overfit if the dataset is small or noisy, 
  and it’s sensitive to outliers (e.g., a student who studies 10 hours but scores poorly due to 
  external factors).
</p>
<h4><b>Lasso Regression (L1 Regularization)</b></h4><br>
<b><h4>Concept</h4></b><br>
Lasso Regression adds an L1 penalty to the Linear Regression cost function:<br>
<i>J(β₀, β₁) = (1/m) Σ(yᵢ - ŷᵢ)² + α |β₁|</i><br>
- <i>α</i>: Regularization parameter (controls penalty strength).<br>
- <i>|β₁|</i>: Absolute value of the coefficient.<br>
<b><h4> Mechanism</h4></b><br>
The L1 penalty encourages sparsity by shrinking <i>β₁</i> to zero if study hours are deemed irrelevant. In this single-variable case, this effect is limited, but Lasso becomes powerful with multiple features (e.g., adding sleep hours or attendance), as it can eliminate less important features.<br>
<b> <h4>Benefits</h4></b><br>
- <b>Feature Selection</b>: Sets coefficients to zero, simplifying the model (useful for future multi-feature scenarios).<br>
- <b>Overfitting Prevention</b>: Reduces <i>β₁</i>, making the model less sensitive to noise.<br>
- <b>Interpretability</b>: Focuses on the most impactful features (e.g., study hours over less relevant factors).<br>
<b><h4>Practical Implications</h4></b><br>
For student performance prediction, Lasso ensures the model doesn’t overfit to noisy data (e.g., outliers like a student who studies little but scores high due to prior knowledge). The <i>α</i> parameter allows tuning: a small <i>α</i> (e.g., 0.1) applies light regularization, while a large <i>α</i> (e.g., 5.0) may overly simplify the model.</p>