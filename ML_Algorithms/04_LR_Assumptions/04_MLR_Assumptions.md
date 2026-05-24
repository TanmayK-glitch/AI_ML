# Top 5 Assumptions of Linear Regression

## Why Assumptions Matter
- OLS (Ordinary Least Squares) gives **BLUE** (Best Linear Unbiased Estimator) only when assumptions hold
- Violated assumptions → biased/inefficient coefficients → bad predictions

---

## 1. Linearity
- Relationship between X and y must be **linear**
- **Check:** Scatter plot of features vs target; residual plot (should show no pattern)
- **Fix:** Log/sqrt transform on X or y; try polynomial features

---

## 2. Multicollinearity
- Independent variables must **not** be highly correlated with each other
- Inflates standard errors → unstable, uninterpretable coefficients

### Check
```python
from statsmodels.stats.outliers_influence import variance_inflation_factor

vif = []
for i in range(X_train.shape[1]):
    vif.append(variance_inflation_factor(X_train, i))

pd.DataFrame({'vif': vif}, index=df.columns[0:3]).T
```
| | feature1 | feature2 | feature3 |
|---|---|---|---|
| vif | 1.01 | 1.01 | 1.01 |

- **VIF < 5** → OK
- **VIF 5–10** → moderate (concern)
- **VIF > 10** → serious multicollinearity

Also check: **Correlation heatmap** — `sns.heatmap(df.corr(), annot=True)`

### Fix
- Drop one of correlated features
- PCA / dimensionality reduction
- Ridge Regression

---

## 3. Independence of Errors (No Autocorrelation)
- Residuals must be **independent** (no pattern over time/order)
- Common in time-series data

### Check
```python
from statsmodels.stats.stattools import durbin_watson
dw = durbin_watson(model.resid)
# ~2 = no autocorrelation | <1 or >3 = problem
```

### Fix
- Add lag features
- Use time-series models (ARIMA etc.)

---

## 4. Homoscedasticity
- Variance of residuals must be **constant** across all predicted values
- Opposite = **heteroscedasticity** (variance fans out)

### Check
```python
# Residuals vs Fitted plot
plt.scatter(model.fittedvalues, model.resid)
plt.axhline(0, color='red')
```
- Random scatter around 0 = good
- Funnel shape = heteroscedasticity

### Fix
- Log/sqrt transform on y
- Weighted Least Squares

---

## 5. Normality of Residuals
- Residuals (errors) must follow **normal distribution**
- Required for valid hypothesis tests and confidence intervals (not for predictions themselves)

### Check
```python
# Q-Q Plot
import scipy.stats as stats
stats.probplot(model.resid, plot=plt)

# Or histogram
plt.hist(model.resid, bins=30)
```
- Straight diagonal line in Q-Q = normal
- Curved/S-shape = non-normal

### Fix
- More data
- Remove outliers
- Transform y variable

---

## Quick Reference Table

| # | Assumption | Check Tool | Fix |
|---|---|---|---|
| 1 | Linearity | Scatter / Residual plot | Transform X or y |
| 2 | No Multicollinearity | VIF, Heatmap | Drop feature, PCA, Ridge |
| 3 | Independence | Durbin-Watson (~2) | Lag features, ARIMA |
| 4 | Homoscedasticity | Residuals vs Fitted | Log(y), WLS |
| 5 | Normal Residuals | Q-Q Plot, Histogram | Remove outliers, Transform y |

---

## Code Imports Cheatsheet
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.linear_model import LinearRegression
import statsmodels.api as sm
from statsmodels.stats.outliers_influence import variance_inflation_factor
from statsmodels.stats.stattools import durbin_watson
import scipy.stats as stats
```
