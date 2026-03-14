# Latent Factor Modelling Of Equity Markets

This project analyzes more than two decades (2000–2024) of U.S. large‑cap stock returns across 8 sectors to uncover hidden systematic risk factors using an EM‑based latent factor model.

---

## Key Findings

- Dominant Financials Factor  
  Factor 1 explains roughly 21 percent of total variance and loads heavily on GS, JPM, and AXP. This indicates that a large share of portfolio risk effectively comes from exposure to the Financials sector.

- Sector‑Tilt Factors  
  Factors 2–10 behave as sector‑tilt factors rather than generic market noise. They are dominated by:
  - Energy: examples include CVX, XOM, COP  
  - Healthcare: examples include JNJ, UNH  
  - Industrials: examples include CAT, GE  
  - Communication: examples include VZ, T  
  - Materials and other cyclicals  

- Crisis Correlation  
  All factors exhibit strong, simultaneous spikes during the Global Financial Crisis (around 2008–2009) and the COVID crash (around 2020). This shows that sector diversification breaks down in systemic stress, as latent factors become highly correlated precisely when risk is highest.

---
## Core Visuals

- Latent Factors Over Time (2000–2024)  
  Shows standardized factor scores and highlights periods where all factors co‑move, such as during 2008 and 2020.
  ![Latent Factors Over Time](images/factor_year.jpg)

- Sector Exposure Heatmap
  Displays average factor loadings by sector, making it easy to see which factors correspond to Financials, Energy, Healthcare, and other sectors.
  ![Sector Exposure Heatmap](images/factor_heat.jpeg)

- Factor Interpretation Table
  Summarizes each factor with its dominant sector, top stocks, and percentage of variance explained.
  ![Factor Interpretation Table](images/factor_table.jpeg)


## Methodology

1. Database Construction  
   Large‑cap U.S. stocks across eight sectors:
   - Technology  
   - Financials  
   - Energy  
   - Consumer  
   - Healthcare  
   - Industrials  
   - Materials  
   - Communication  

2. Pipeline  
   - Download daily adjusted close prices from 2000‑01‑01 to 2024‑01‑01 using `yfinance`.  
   - Compute log returns for each stock.  
   - Standardize returns so that each stock has zero mean and unit variance.

3. Latent Factor Model (EM Factor Analysis)  
   - Implement Expectation–Maximization for factor analysis from scratch using NumPy.  
   - Initialize factor loadings via singular value decomposition (SVD) of the return covariance matrix.  
   - E‑step: compute expected latent factors and their second moments for the standardized return matrix.  
   - M‑step: update factor loadings and stock‑specific variances, iterating until convergence.  
   - Outputs:
     - Factor scores (time series of latent factors).  
     - Stock‑by‑factor loading matrix.  
     - Idiosyncratic (stock‑specific) noise variances.

4. Interpretation Tools  
   - Factor time series plots to inspect volatility regimes and crisis periods.  
   - Sector exposure heatmap to visualize average factor loadings by sector.  
   - Factor interpretation table that lists, for each factor, its dominant sector, top three stocks by absolute loading, and variance contribution.

---


