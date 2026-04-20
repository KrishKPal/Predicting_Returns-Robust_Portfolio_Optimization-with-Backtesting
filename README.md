This repository contains my work for the Predict2Optimize / WiDS program, covering both theory and coding tasks from Week 1 to Week 5.

The focus of this project was not to build a profitable trading strategy,but to understand how portfolio optimization behaves when it is run over
time using realistic assumptions such as noisy predictions, rebalancing,and transaction costs.

The main goal was to develop discipline in evaluation, understand the limits of financial prediction, and avoid common pitfalls such as look-ahead bias and overfitting.


# Week 1: Basic Financial Data Analysis

Assets used (across total weeks):
• AAPL, MSFT, GOOG, AMZN, TSLA 

Time horizons studied:
1. Long-term: 2015 to 2024
2. Medium-term: 2020 to 2024 ( voilatile period like covid studied)

Concepts Used:
1. Adjusted Close prices 
2. Simple returns and log returns  
3. Rolling volatility (standard deviation)
4. Rolling mean and variance analysis

Inference:
1. Prices are non-stationary, while returns are approximately stationary
2. Volatility changes heavily due to market stress

# Week 2: Baseline Prediction Models & Evaluation
Financial return prediction can be extremely noisy. 
Before using complex models, it is important to establish strong naive baselines.

Models implemented:
1. Zero-return predictor  
   a strong sanity check baseline ,assumes zero return change everytime.

2. Rolling mean predictor  
   Uses recent average returns to predict the next period.

3. OLS (Linear Regression)  
    Today’s return, Yesterday's return, 20-day rolling mean, 20-day rolling volatility, 5-day momentum etc.

 Time Evaluation method:
1. Walk-forward (TimeSeriesSplit) used instead of random test splits
2.  MSE and RMSE , I used MSE as metric for calculation. Either of the choice does not change the absolute result.

Results (approx):
• Zero predictor ≈ 0.0186  
• Rolling mean ≈ 0.0190  
• OLS ≈ 0.0187  

Inference:
Simple baselines do perform surprisingly well, Rolling mean predictor performed quite well while other models were close.

# Week 4: Portfolio Optimization

Topics covered:
1. Equal Weights Baseline
2. Mean–variance (Markowitz) portfolio optimization
3. Global Minimum Variance Portfolio (GMVP)
4. Constrained optimization 
5. Robust optimization to account for uncertainty in expected returns

Inference:
Mean estimations are noisy and can lead to unstable portfolio returns while Robust optimization can help in controlling and optimizing extreme data over a period of time.

---
## Week 5: Integration and Backtesting ( Final Submission )

In the final task, all components were combined :

1. Estimate expected returns and covariance using past data
2. Compute portfolio weights using optimization
4. Rebalance periodically
5. Account for the transaction costs using turnover
6. Track portfolio wealth over time
7. Equal-weight (1/N) baseline portfolio
8. Robust Markowitz portfolio using convex optimization

Backtesting details:
1. Walk-forward evaluation
2. Monthly rebalancing
3. Turnover-based transaction costs


Final Results:
Both strategies achieved nearly similar performance over the test period.
My robust strategy do produce smoother weight changes, but did not significantly outperform the equal-weight baseline
This highlights that robustness and stability are often more important to optimize portfolio rather than trying to extractall the small predictive signals.

This project is intended purely for learning purposes.As the strategy used here are not useful or good for real life trading , its just a simple basic model of how wealth can be added up and grown with small significant returns and changes in market .



