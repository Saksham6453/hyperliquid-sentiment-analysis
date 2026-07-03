# hyperliquid-sentiment-analysis

## 📌 Executive Summary
This project analyzes the relationship between high-frequency proprietary trader performance data from Hyperliquid and the daily Bitcoin Fear & Greed Index. By merging execution-level logs with daily macroeconomic sentiment indicators, this analysis uncovers critical behavioral patterns, strategy alpha windows, and structural friction points (such as execution fee drag). 

The core finding reveals that the trading strategy is highly optimized for strong momentum environments, exhibiting exceptional efficiency during **Extreme Greed** phases, while experiencing sharp win-rate compression and capital decay during panic-driven **Extreme Fear** liquidations.

---

## 📊 Core Performance Metrics

The following comprehensive breakdown summarizes trading activity, profitability, and cost structures across all primary market sentiment classifications:

| Market Sentiment Phase | Total Executed Trades | Win Rate (%) | Profit Factor | Average PnL (USD) | Total Net PnL (USD) | Total Fees Paid (USD) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 🟢 **Extreme Greed** | 39,992 | 46.49% | 11.02 | $67.89 | $2,715,171.31 | $27,030.67 |
| 🟡 **Greed** | 50,303 | 38.48% | 3.03 | $42.74 | $2,150,129.27 | $63,098.69 |
| ⚪ **Neutral** | 37,686 | 39.70% | 4.32 | $34.31 | $1,292,920.68 | $39,374.27 |
| 🟠 **Fear** | 61,837 | 42.08% | 6.66 | $54.29 | $3,357,155.44 | $92,456.95 |
| 🔴 **Extreme Fear** | 21,400 | 37.06% | 2.16 | $34.54 | $739,110.25 | $23,888.63 |

---

## 🔍 Key Data Insights & Hidden Patterns

### 1. The Momentum Alpha Window ("Extreme Greed")
Contrary to retail market behavior, which frequently fights the trend or suffers from late FOMO drawdowns at local tops, the strategy deployed here exhibits pure momentum alpha. 
* **Insight:** During **Extreme Greed**, the system prints its highest standalone **Win Rate (46.49%)** and a staggering **Profit Factor of 11.02**. 
* **Takeaway:** This proves the core strategy excels at identifying and holding strong directional breakouts on Hyperliquid when market participant velocity is highest.

### 2. High-Frequency Friction & Fee Drag in "Fear"
The data shows that market volatility during general **Fear** phases induces the highest frequency of trading activity.
* **Insight:** General **Fear** phases generated the highest volume of positions with **61,837 trades**, accumulating **$92,456.95** in total protocol fees. 
* **Takeaway:** While the Total PnL remains high ($3.35M), the excessive turnover introduces significant fee drag. The fee-to-PnL ratio is noticeably less efficient than the clean, high-conviction executions observed during Extreme Greed.

### 3. Structural Breakdown under "Extreme Fear"
There is a severe non-linear shift in performance when the market drops from a cautious "Fear" state into outright panic.
* **Insight:** During **Extreme Fear**, the strategy's **Win Rate collapses to its lowest absolute point (37.06%)**, and the **Profit Factor drops to 2.16**. 
* **Takeaway:** The sharp decline indicates that under generalized cascade liquidations and forced selling conditions, the strategy's directional triggers break down or experience high slippage.

---

## 💡 Strategic Trading Recommendations

Based on the empirical insights derived from the historical data, the following system optimizations are recommended to drive smarter trading execution:

1. **Dynamic Capital Allocation & Sizing Matrix:** Implement a systematic parameter filter tied directly to the daily Fear & Greed Index. Sizing should be aggressively scaled up during strong trend expansions (**Extreme Greed** index values > 75) and dynamically scaled down or paused when the index triggers an **Extreme Fear** print (< 25).
2. **Execution Fee Optimization:** Given the massive absolute transaction costs incurred during high-turnover **Fear** regimes ($92k+ paid), the execution routing engine should transition from heavy Taker profiles (market orders) to passive Maker layouts (post-only limit orders) to capture Hyperliquid maker fee structures.
3. **Volatility Regimes Adjustments:** The strategy requires tighter tracking or trailing stop-losses during deep panic windows to eliminate systemic downside tail risk when asset correlations snap to 1.

---

## 🛠️ Tech Stack & Methodology
* **Language:** Python
* **Libraries Used:** `pandas` (Data alignment & matrix aggregation), `numpy` (Mathematical structures), `matplotlib` & `seaborn` (Statistical data plotting).
* **Timeframe Alignment:** Reconciled high-frequency millisecond execution tracking timestamps (`Timestamp IST`) to the global daily sentiment indexes using custom date-boundary masking.
