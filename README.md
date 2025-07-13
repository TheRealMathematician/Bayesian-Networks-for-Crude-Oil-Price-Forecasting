# Bayesian-Networks-for-Crude-Oil-Price-Forecasting
# 📊 Hybrid Probabilistic Modeling for Crude Oil Price Forecasting

## 🧠 Background and Overview

This project implements a **hybrid probabilistic graphical modeling framework** for **crude oil price forecasting**, combining:

* ⚖️ **Bayesian Belief Networks (BBNs)**: Captures causal dependencies among oil price drivers
* ⚛️ **Hidden Markov Models (HMMs)**: Detects regime shifts in price behavior (Bull, Bear, Stagnant)

📚 Inspired by Alvi's (2018) foundational research, our approach aims to overcome the **limitations of traditional econometric models** (like GARCH/ARMA) by modeling **non-linear relationships** and **market regimes** more effectively.

---

## 📂 Data Structure Overview

### 🚗 Core Datasets

* **Brent Crude Oil Prices (POILBREUSDM)**
* **Time Range**: 2010–2023 (Daily)
* **Source**: FRED Economic Data
* **Complementary Series**: OVX (Oil Volatility Index)

### ⚒️ Key Transformations

* HMM-based regime classification (Bull / Bear / Stagnant)
* Feature discretization for BBN compatibility
* Structural learning via **hill climbing**
* Parameter estimation with **maximum likelihood**
* Train/validation/test splits: **70/15/15**

---

## 👩‍💼 Executive Summary

### 🚀 Key Results and Findings

1. **📊 Model Accuracy & Trends**

   * **79.4% regime classification accuracy**
   * Strong predictive performance during **volatility spikes** (e.g., 2015 oil crash)
   * Outperformed ARMA and GARCH-M in bear markets by **12%**

2. **🔧 Training Performance**

   * Optimal BBN structure: **3 nodes, 2 edges**
   * Hill climbing converged in <50 iterations
   * **BIC** scoring balanced complexity and overfitting

3. **📊 Validation Insights**

   * Early stopping triggered at **iteration 42** (min validation loss)
   * Maintained stability across **market regimes**
   * **15% validation set** reduced overfitting risk

4. **⚔️ Comparative Performance**

| Metric             | Our Model | GARCH-M | ARMA  |
| ------------------ | --------- | ------- | ----- |
| Regime Accuracy    | **79.4%** | 67.2%   | 58.9% |
| Volatility Capture | **82%**   | 75%     | 63%   |
| Bull Market RMSE   | **1.24**  | 1.45    | 1.67  |
| Bear Market RMSE   | **1.07**  | 1.32    | 1.55  |

---

## 🔬 Insights Deep Dive

### 🧮 Algorithm Analysis

1. **Hill Climbing for BBN**

   * Efficient **greedy search** for network structure
   * BIC scoring penalized over-complex graphs
   * Used **random restarts** to avoid local optima

2. **HMM-BBN Integration**

   * HMM discretized price behavior into 3 regimes
   * BBN learned conditional dependencies (e.g., OVX → Crude movement)
   * Synergy enabled regime-aware structural learning

3. **Market Regime Performance**

   * Best results in **Bear markets**: 87% accuracy
   * Reasonable in **Stagnant**: 73%
   * Detected regime transitions with minimal lag

4. **🚀 Computational Efficiency**

   * Full training completed in **<5 minutes** on standard laptop
   * Tools: `pgmpy`, `hmmlearn`
   * Model scales well to high-dimensional input

---

## ✅ Final Recommendations

### ⚙️ Implementation Strategy

1. **Production Deployment**

   * Daily rolling window (5 years) for model refresh
   * Cloud-based **parallel hill climbing** optimization
   * Integrate **real-time HMM regime monitor**

2. **Risk Management Applications**

   * Set **confidence thresholds** for actionable signals
   * Use model averaging in high-volatility periods
   * Fallback to ARMA/GARCH during data outages

3. **Model Enhancement Plan**

   * Include **macroeconomic indicators** (GDP, inflation)
   * Add **sentiment features** from oil headlines/news APIs
   * Explore ensemble modeling and dynamic structure selection

---

## 🌐 Future Enhancements

1. Expand model to **multi-commodity datasets** (e.g., Natural Gas, WTI)
2. Explore **deep HMM** variants (e.g., HMM-RNN hybrids)
3. Implement **Bayesian hyperparameter optimization**
4. Design **interactive dashboards** for regime visualization
5. Automate **structural re-learning** during regime shifts

---
