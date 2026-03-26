# Algeria’s GDP Using Time Series Analysis

## ARIMA Time Series Analysis of Algeria GDP

### Phase I: Identification
<img width="952" height="507" alt="image" src="https://github.com/user-attachments/assets/066963eb-23fc-4687-a630-0b668bf85c25" />

#### Data Preparation
* **Log Transformation:** A logarithmic transformation was applied to stabilize the variance of the GDP series and reduce the effect of exponential growth.
  <img width="952" height="507" alt="image" src="https://github.com/user-attachments/assets/3ee196c1-d3aa-47eb-8e6a-f6237e5beb26" />

* **Differencing to Remove Trend:** The first difference of the log-transformed GDP series was taken to remove the trend and achieve stationarity.
  <img width="952" height="507" alt="image" src="https://github.com/user-attachments/assets/7a5fe1b7-4134-424f-9cff-aa576a631cc3" />

* **Stationarity Test (Augmented Dickey-Fuller):** The ADF test on the first-differenced log GDP series produced a p-value of 0.4408 (> 0.05), indicating failure to reject the null hypothesis of a unit root. The series remained non-stationary. After a second differencing, the series became stationary.
  <img width="937" height="173" alt="image" src="https://github.com/user-attachments/assets/2f45eac6-c8a2-4d27-b4ae-30d5be041889" />
  <img width="930" height="532" alt="image" src="https://github.com/user-attachments/assets/1068f256-dc4f-4db6-b624-a62eda7ee285" />

  
#### Model Selection
* **ACF and PACF Analysis:** - ACF indicates a MA(1) component.
  - PACF shows significant spikes at lags 2 and 3, suggesting AR(2–3) components.
    <img width="930" height="532" alt="image" src="https://github.com/user-attachments/assets/3928f108-883d-4b2f-a9a4-2271441f9b0d" />
    <img width="930" height="532" alt="image" src="https://github.com/user-attachments/assets/ed7e9dae-84b9-4768-a9b7-e30e83680ba3" />

* **Candidate Models:** - ARIMA(2,2,1)
  - ARIMA(3,2,1)


---

### Phase II: Estimation and Testing

#### Estimation
* **Chosen Model:** ARIMA(3,2,1)
* **Estimated Parameters:**

| Parameter | Value |
| :--- | :--- |
| AR1 | -1.1903 |
| AR2 | -0.9793 |
| AR3 | -0.4555 |
| MA1 | -1.0000 |
| Residual Variance (σ²) | 0.02823 |
<img width="931" height="607" alt="image" src="https://github.com/user-attachments/assets/90060837-85ee-4ed8-8aeb-a82fb0c7ccd2" />

#### Diagnostic Analysis
* **Residuals Analysis:**
  <img width="927" height="555" alt="image" src="https://github.com/user-attachments/assets/d7097790-30dc-4cef-882b-8ddcbcff536b" />
  <img width="927" height="555" alt="image" src="https://github.com/user-attachments/assets/84a93c82-2dde-4f60-ae12-a78f125cf12b" />
  <img width="927" height="555" alt="image" src="https://github.com/user-attachments/assets/8fdb8698-7e76-4595-af97-9b76c00d9e57" />

  - **Normality Check:** Shapiro-Wilk test: W = 0.978, p = 0.308. Residuals approximately normal according to QQ plot and histogram.
  - **Independence Check:** Box-Ljung test: X² = 39.42, df = 20, p = 0.0059. Residuals show significant autocorrelation, indicating remaining temporal dependencies.

---

### Conclusion
* The ARIMA(3,2,1) model fits the GDP series reasonably well in terms of normality and capturing overall trends.
* However, residuals exhibit significant autocorrelation and are not white noise.
* Therefore, we cannot proceed to the forecasting phase without further refinement.
