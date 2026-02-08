# A Comparative Analysis: ARIMA vs ETS vs Prophet in forecasting Ghana's GDP (1960 - 2023) 

[![R](https://img.shields.io/badge/R-276DC3?style=flat&logo=r&logoColor=white)](https://www.r-project.org/)
[![RStudio](https://img.shields.io/badge/RStudio-75AADB?style=flat&logo=rstudio&logoColor=white)](https://rstudio.com/)

Time series forecasting analysis comparing ARIMA, ETS, and Prophet models using 63 years of Ghana's GDP data (1960-2023).

** [View Full Analysis Report (HTML)](A-Comparative-Analysis-of-ARIMA,-Exponential-Smoothing-and-Prophet-on-the-forecasting-of-Ghana-s-GDP.html)**

---

##  Project Overview

This project compares three time series forecasting approaches:
- **ARIMA(1,2,3)** - Auto-Regressive Integrated Moving Average
- **ETS** - Exponential Smoothing State Space Model  
- **Prophet** - Facebook's forecasting algorithm

**Key Finding:** Prophet outperformed SARIMA by 27% and ETS by 37% based on RMSE evaluation.

---

##  Results Summary

### Model Performance

| Model | RMSE | MAE | Performance vs Prophet |
|-------|------|-----|------------------------|
| Prophet ⭐ | 6699.42 | 6719.49 | Best (Baseline) |
| ARIMA | 9145.93 | 9185.03 | -27% worse |
| ETS | 10643.89 | 10701.65 | -37% worse |

### Key Visualizations

**GDP Historical Trend (1960-2023)**
![GDP Trend](outputs/figures/gdp_historical_trend.png)

**SARIMA Forecast**
![SARIMA](outputs/figures/sarima_forecast.png)

**ETS Forecast**
![ETS](outputs/figures/ets_forecast.png)

**Prophet Forecast**
![Prophet](outputs/figures/prophet_forecast_vs_actual.png)

**Model Performance Comparison**
![Comparison](outputs/figures/model_comparison.png)

---

##  Key Insights

1. **Prophet's Advantage:** Better handling of structural breaks in Ghana's economic history (e.g., 1983 economic crisis, 2008 financial crisis)

2. **SARIMA Limitation:** Assumes stationary patterns after differencing; struggles with Ghana's volatile economic trajectory

3. **ETS Performance:** Simple exponential smoothing insufficient for complex economic trends with multiple structural changes

4. **Policy Recommendation:** Government economic planners should adopt Prophet for 5-year GDP forecasting cycles due to its superior accuracy and robustness to economic shocks

---

## 🛠 Technical Approach

### Data
- **Source:** World Bank Open Data (NY.GDP.MKTP.CD)
- **Period:** 1960-2023 (63 annual observations)
- **Train/Test Split:** 80/20 (1960-2010 training, 2011-2023 testing)

### Methodology

#### ARIMA(1,2,3)
- Stationarity testing: ADF and KPSS tests
- Differencing order: d=2 (determined by `ndiffs()`)
- ACF/PACF analysis for parameter selection
- Validated with `auto.arima()` comparison

#### ETS
- Automatic model selection using AIC
- Error, Trend, Seasonality components optimized
- Residual diagnostics with Ljung-Box test

#### Prophet
- Automatic changepoint detection
- Yearly seasonality enabled
- Handles structural breaks and missing data
- Robust to outliers

### Evaluation Metrics
- **RMSE** (Root Mean Squared Error): Penalizes large errors
- **MAE** (Mean Absolute Error): Average magnitude of errors

---

##  Project Structure
```
ghana-gdp-forecasting/
├── README.md
├── A Comparative Analysis of ARIMA, Exponential Smoothing and Prophet on the forecasting of Ghana's GDP.Rmd       # R Markdown analysis
├── A-Comparative-Analysis-of-ARIMA,-Exponential-Smoothing-and-Prophet-on-the-forecasting-of-Ghana-s-GDP.html      # Knitted HTML report
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

##  How to Reproduce

### Prerequisites
```r
install.packages(c(
  "ggplot2",
  "astsa",
  "forecast", 
  "tseries",
  "prophet",
  "tibble"
))
```

### Run Analysis

1. Clone this repository
```bash
git clone https://github.com/yourusername/ghana-gdp-forecasting.git
cd ghana-gdp-forecasting
```

2. Open `gdp_forecasting_analysis.Rmd` in RStudio

3. Click **"Knit"** or run:
```r
rmarkdown::render("gdp_forecasting_analysis.Rmd")
```

---

##  Data Source

**World Bank Open Data**
- Indicator: NY.GDP.MKTP.CD (GDP, current US$)
- Country: Ghana
- URL: https://data.worldbank.org/indicator/NY.GDP.MKTP.CD?locations=GH
- Download Date: September 2025

---

## Skills Demonstrated

✅ Time series analysis (stationarity testing, differencing)  
✅ Statistical modeling (SARIMA, ETS)  
✅ Machine learning (Prophet)  
✅ Model evaluation and comparison  
✅ Data visualization in R (ggplot2)  
✅ Residual diagnostics  
✅ Economic data analysis  
✅ R Markdown documentation  
✅ Reproducible research  

---

## References

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

## 📄 License

This project is open source and available under the MIT License.

---

*Completed as part of BSc Statistics (Data Science) final year project at Kwame Nkrumah University of Science and Technology, Ghana (May - September 2025)*
```