

**Step 1** — Upload Dataset  
Click the **"Upload Dataset"** button and select your CSV file. The dataset must contain the following columns:  
`ID`, `Student Name`, `Study Hours`, `Attendance %`, `Previous Score`, and `Exam Score`.

![Step 1: Upload Dataset](./images/Step-1.png)

**Step 2** — Dataset Preview  
After successful upload, a preview of the raw dataset will appear. Review the data, then click **"NEXT"** to proceed to the data cleaning stage.

![Step 2: Dataset Preview](./images/Step-2.png)

**Step 3** — Data Cleaning  
Click **"Clean & Update Dataset"** to automatically handle missing values, outliers, and inconsistencies. The cleaned dataset will be displayed. Once satisfied, click **"NEXT"**.

![Step 3: Data Cleaning](./images/Step-3.png)

**Step 4** — Train-Test Split  
Use the slider to set the desired train-test split ratio (recommended: **80% training / 20% testing**). After adjusting, click **"NEXT"** to proceed.

![Step 4: Train-Test Split](./images/Step-4.png)

**Step 5** — Apply Linear Regression  
The app now trains a **Linear Regression** model. Training and testing **\(R^2\)** scores are displayed.  
If there is a large gap between training and testing \(R^2\) (indicating overfitting), proceed to the next steps.

![Step 5: Linear Regression Results](./images/Step-5.png)

**Step 6** — Apply Lasso Regression (L1 Regularization)  
Tune the **alpha (α)** parameter using the slider to control regularization strength. The app shows the best alpha and corresponding \(R^2\) scores. Compare performance with Linear Regression, then click **"Go to Ridge Regression"**.

![Step 6: Lasso Regression](./images/Step-6.png)

**Step 7** — Apply Ridge Regression (L2 Regularization)  
Adjust the **alpha (α)** value to minimize overfitting while maintaining predictive power. Observe the optimal \(R^2\) score, then click **"Compare All Regressions"**.

![Step 7: Ridge Regression](./images/Step-7.png)

**Step 8** — Final Model Comparison  
All three models (Linear, Lasso, Ridge) are compared side-by-side based on:  
- Training \(R^2\)  
- Testing \(R^2\)  
- Best alpha (for Lasso & Ridge)  
The **best-performing model** is automatically highlighted.

![Step 8: Model Comparison](./images/Step-8.png)

