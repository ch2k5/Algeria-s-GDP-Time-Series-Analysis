# Algeria-s-GDP-Using-Time-Series-Analysis

ARIMA Time Series Analysis of Algeria GDP
Phase I: Identification
Data Preparation
Log Transformation:
A logarithmic transformation was applied to stabilize the variance of the GDP series and reduce the effect of exponential growth.
Differencing to Remove Trend:
The first difference of the log-transformed GDP series was taken to remove the trend and achieve stationarity.
Stationarity Test (Augmented Dickey-Fuller):
The ADF test on the first-differenced log GDP series produced a p-value of 0.4408 (> 0.05), indicating failure to reject the null hypothesis of a unit root. The series remained non-stationary. After a second differencing, the series became stationary.
Model Selection
ACF and PACF Analysis:
ACF indicates a MA(1) component.
PACF shows significant spikes at lags 2 and 3, suggesting AR(2–3) components.
Candidate Models:
ARIMA(2,2,1)
ARIMA(3,2,1)
The ARIMA(3,2,1) model is preferred due to better fit without overfitting.
Phase II: Estimation and Testing
Estimation

Chosen Model: ARIMA(3,2,1)

Estimated Parameters:

Parameter	Value
AR1	-1.1903
AR2	-0.9793
AR3	-0.4555
MA1	-1.0000
Residual Variance (σ²)	0.02823

Training Set Error Measures:

Metric	Value
RMSE	0.1598
MAE	0.1270
Diagnostic Analysis

Residuals Analysis:

Normality Check:
Shapiro-Wilk test: W = 0.978, p = 0.308
Residuals approximately normal according to QQ plot and histogram.
Independence Check:
Box-Ljung test: X² = 39.42, df = 20, p = 0.0059
Residuals show significant autocorrelation, indicating remaining temporal dependencies.
Conclusion
The ARIMA(3,2,1) model fits the GDP series reasonably well in terms of normality and capturing overall trends.
However, residuals exhibit significant autocorrelation and are not white noise.
Therefore, we cannot proceed to the forecasting phase without further refinement.
