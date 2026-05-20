## Regression Metrices
- Mean ways to check the Accuracy of the LR Model

1. Mean Absolute Error(MAE)
    - Intuition: MAE measures the average of the absolute differences between the actual data(yi) points and the predictions(yicap) made by your model.
    - Formula: $$ MAE = \frac{1}{n}\sum_{i=1}^{n} \left| y_i - \hat{y}_i \right| $$ 
    - Advantages: The biggest advantage is that the result is in the same unit as your output column. If you are predicting a salary package in LPA (Lakhs Per Annum), an MAE of 1.5 means your model is off by 1.5 LPA on average. It is also robust to outliers. 
    - Disadvantages: The modulus function (∣x∣) creates a sharp V-shaped graph that is not differentiable at zero. Because optimization techniques like Gradient Descent require calculating derivatives to find the minimum error, MAE is difficult to use directly as a loss function for training.

2. Mean Squared Error(MSE)
    - Intuition: Instead of taking the absolute value, MSE squares the errors before averaging them. Geometrically, it calculates the area of squares drawn between the actual points and the predicted line.
    - Advantages: Because it uses a square function, the resulting curve (a parabola) is smooth and differentiable at all points. This makes it an ideal loss function for algorithms that rely on calculus to minimize error
    -  It changes the unit of the error. If predicting LPA, the MSE unit becomes LPA Square which is very difficult to interpret in real-world terms

3. Root Mean Squared Error(RMSE)
    - RMSE is simply the square root of MSE
    - Advantages: By taking the square root, it brings the error back to its original unit (e.g., LPA), making it much easier to interpret while retaining the differentiability benefits of MSE
    - Disadvantages: Like MSE, it is still sensitive to outliers because the squaring happens before the root

4. R2 Score (Coefficient of Determination)
    - Intuition: While MAE, MSE, and RMSE give you absolute error values (which depend entirely on the context of the data), the R2
    Score is context-independent.
    If your R2 score is 0.80, it means 80% of the variance (the differences in the output) is successfully explained by your input feature(s) The remaining 20% is due to unknown factors.
    - Disadvantage: The Major Flaw: If you add completely irrelevant input columns to your dataset (like "the temperature on the day of an interview"), the R2
    score will falsely remain the same or even increase.

