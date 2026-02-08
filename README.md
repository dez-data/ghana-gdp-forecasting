# A Comparative Analysis: ARIMA vs ETS vs Prophet in Forecasting Ghana's GDP (1960 - 2023) 

[![R](https://img.shields.io/badge/R-276DC3?style=flat&logo=r&logoColor=white)](https://www.r-project.org/)
[![RStudio](https://img.shields.io/badge/RStudio-75AADB?style=flat&logo=rstudio&logoColor=white)](https://rstudio.com/)

Time series forecasting analysis comparing ARIMA, ETS, and Prophet models using 63 years of Ghana's GDP data (1960-2023).

**[View Full Analysis Report (HTML)](https://dez-data.github.io/ghana-gdp-forecasting/A-Comparative-Analysis-of-ARIMA,-Exponential-Smoothing-and-Prophet-on-the-forecasting-of-Ghana-s-GDP.html)**

---

## Project Overview

This project compares three time series forecasting approaches:
- **ARIMA(1,2,3)** - Auto-Regressive Integrated Moving Average
- **ETS** - Exponential Smoothing State Space Model  
- **Prophet** - Facebook's forecasting algorithm

**Key Finding:** Prophet outperformed ARIMA by 27% and ETS by 37% based on RMSE evaluation, making it the optimal model for Ghana's GDP forecasting.

---

## Results Summary

### Model Performance

| Model | RMSE | MAE | Performance vs Prophet |
|-------|------|-----|------------------------|
| Prophet | 6,699 | 6,719 | Best (Baseline) |
| ARIMA(1,2,3) | 9,146 | 9,185 | -27% worse |
| ETS | 10,644 | 10,702 | -37% worse |

### Key Visualizations

**Ghana's GDP Historical Trend (1960-2023)**
![GDP Trend](outputs/figures/Ghana's%20GDP%20Series%20(1960%20-%202023).png)

**ARIMA Forecast**
![ARIMA](outputs/figures/GDP%20Forecast%20by%20ARIMA.png)

**ETS Forecast**
![ETS](outputs/figures/GDP%20Forecast%20by%20ETS.png)

**Prophet Forecast**
![Prophet](outputs/figures/GDP%20Forecast%20by%20Prophet.png)

**Model Performance Comparison - RMSE**
![RMSE Comparison](outputs/figures/comparison%20by%20rmse.png)

**Model Performance Comparison - MAE**
![MAE Comparison](outputs/figures/comparison%20by%20mae.png)

---

## Key Insights

1. **Prophet's Superior Performance:** 
   - 27% lower error rate than ARIMA (RMSE: 6,699 vs 9,146)
   - 37% lower error rate than ETS (RMSE: 6,699 vs 10,644)
   - Consistent advantage across both RMSE and MAE metrics

2. **Why Prophet Won:**
   - Better handling of structural breaks in Ghana's economic history (e.g., 1983 economic crisis, 2008 financial crisis)
   - Automatic changepoint detection adapts to regime changes
   - Robust to outliers and missing data

3. **ARIMA Limitation:** 
   - Assumes stationary patterns after differencing (d=2 required)
   - Struggles with Ghana's volatile economic trajectory and multiple structural changes
   - Best suited for more stable economic environments

4. **ETS Performance:** 
   - Simple exponential smoothing insufficient for complex economic trends
   - Cannot adequately capture long-term structural changes in Ghana's economy
   - Weakest performer due to inability to handle regime shifts

5. **Policy Recommendation:** 
   - Government economic planners should adopt Prophet for 5-year GDP forecasting cycles
   - Superior accuracy (27-37% improvement) enables better budget planning and policy decisions
   - Model's transparency allows interpretation of trend components and changepoints

---

## Technical Approach

### Data
- **Source:** World Bank Open Data (NY.GDP.MKTP.CD)
- **Period:** 1960-2023 (63 annual observations)
- **Train/Test Split:** (1960-2021 training, 2022-2023 testing)

### Methodology

#### ARIMA(1,2,3)
- **Stationarity Testing:** ADF and KPSS tests showed non-stationarity
- **Differencing Order:** d=2 (determined by `ndiffs()`)
- **ACF/PACF Analysis:** Identified AR(1) and MA(3) components
- **Validation:** Cross-checked with `auto.arima()` recommendations

#### ETS
- **Model Selection:** Automatic selection using AIC criterion
- **Components:** Error, Trend, Seasonality optimized
- **Residual Diagnostics:** Ljung-Box test for independence
- **Result:** Simple exponential smoothing selected

#### Prophet
- **Changepoint Detection:** Automatic identification of structural breaks
- **Seasonality:** Yearly seasonality enabled
- **Flexibility:** Handles missing data and outliers
- **Uncertainty:** 80% and 95% prediction intervals generated

### Evaluation Metrics
- **RMSE** (Root Mean Squared Error): Penalizes large forecast errors
- **MAE** (Mean Absolute Error): Average magnitude of forecast errors
- **Lower values indicate better performance**

---

## Project Structure
```
ghana-gdp-forecasting/
├── README.md
├── A Comparative Analysis of ARIMA, Exponential Smoothing and Prophet on the forecasting of Ghana's GDP.Rmd
├── A-Comparative-Analysis-of-ARIMA,-Exponential-Smoothing-and-Prophet-on-the-forecasting-of-Ghana-s-GDP.html
├── data/
│   └── Ghana_GDP_A.csv               # GDP data (1960-2023)
└── outputs/
    └── figures/
        ├── Ghana's GDP Series (1960 - 2023).png
        ├── GDP Forecast by Prophet.png
        ├── GDP Forecast by ETS.png
        ├── GDP Forecast by ARIMA.png
        ├── comparison by rmse.png
        └── comparison by mae.png
```

---

## 🚀 How to Reproduce

### Prerequisites
```r
install.packages(c(
  "tibble",
  "ggplot2",
  "astsa",
  "forecast", 
  "tseries",
  "prophet"
))
```

### Run Analysis

1. Clone this repository
```bash
git clone https://github.com/dez-data/ghana-gdp-forecasting.git
cd ghana-gdp-forecasting
```

2. Open the `.Rmd` file in RStudio

3. Click **"Knit"** or run:
```r
rmarkdown::render("A Comparative Analysis of ARIMA, Exponential Smoothing and Prophet on the forecasting of Ghana's GDP.Rmd")
```

---

## 📊 Data Source

**World Bank Open Data**
- Indicator: NY.GDP.MKTP.CD (GDP, current US$)
- Country: Ghana
- URL: https://data.worldbank.org/indicator/NY.GDP.MKTP.CD?locations=GH
- Download Date: August 2025

---

## Skills Demonstrated

Time series analysis (stationarity testing, differencing)  
Statistical modeling (ARIMA, ETS)  
Machine learning (Prophet)  
Model evaluation and comparison  
Data visualization in R (ggplot2)  
Residual diagnostics  
Economic data analysis  
R Markdown documentation  
Reproducible research  

---

## 📚 References

- Hyndman, R.J., & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice* (3rd ed.). OTexts.
- Taylor, S.J., & Letham, B. (2018). Forecasting at scale. *The American Statistician*, 72(1), 37-45.
- World Bank. (2023). *World Development Indicators*. https://data.worldbank.org

---

## Author

**Samuel Agondeze Kisoke**  
BSc. Statistics (Data Science Track) | KNUST, Ghana

📧 samuelasteragondeze@gmail.com  
💼 [LinkedIn](https://linkedin.com/in/samuel-agondeze-kisoke)  
🐙 [GitHub](https://github.com/dez-data)

---

## License

This project is open source and available under the MIT License.

---

*Completed as part of BSc Statistics (Data Science) final year project at Kwame Nkrumah University of Science and Technology, Ghana (May - September 2025)*


