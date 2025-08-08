# Triple Barrier Method – Trading Strategy

This repository contains an implementation of the **Triple Barrier Method**, a robust labeling technique for financial time series used in algorithmic and machine learning-based trading strategies.  
It provides more realistic trade outcome labeling by considering **price targets, stop losses, and time constraints** simultaneously.

---

## 1. Purpose of This Repository

In financial machine learning, correctly labeling past trades is essential for building predictive models.  
Traditional labeling often relies on fixed time horizons or single thresholds, which can lead to biased or unrealistic results.  

The **Triple Barrier Method**, introduced in *Advances in Financial Machine Learning* by Marcos López de Prado, improves this by setting three independent exit conditions for trades:

1. **Upper barrier** – Target profit level (*take profit*).  
2. **Lower barrier** – Loss limit (*stop loss*).  
3. **Time barrier** – Maximum allowed holding period.

The trade outcome is determined by **which barrier is hit first**, providing richer and more reliable labels for training models.

---

## 2. Method Description

### How It Works
- **Step 1:** For each starting point in a price series, define:
  - An **upper price threshold** (take profit).
  - A **lower price threshold** (stop loss).
  - A **maximum time limit** (time barrier).
- **Step 2:** Track the price path from the start date until one of these barriers is reached.
- **Step 3:** Assign the label:
  - **+1** if the upper barrier is hit first (profitable trade).
  - **-1** if the lower barrier is hit first (loss-making trade).
  - **0** if the time barrier is reached without hitting either price barrier.

### Key Points
- **Strengths:**
  - Models realistic trading conditions by combining price and time constraints.
  - Avoids bias from fixed time labeling.
  - Captures both direction and magnitude of moves.
- **Limitations:**
  - Requires careful calibration of barrier sizes and time limits.
  - Sensitive to market volatility and price noise.
  - Computationally more intensive than binary labeling.

---

## 3. Repository Structure

```plaintext
Triple-Barrier-Strategy/
│
├── triple-barrier-strat.ipynb    # Jupyter Notebook implementing the method
└── README.md                     # Project documentation
```

## 4. How to Use

1. Open the `triple-barrier-strat.ipynb` notebook in **Jupyter Notebook** or **Google Colab**.
2. Provide your historical price data as a **pandas DataFrame**.
3. Adjust the key parameters:
   - **Upper barrier**: e.g., `+0.02` for a 2% take profit.
   - **Lower barrier**: e.g., `-0.02` for a 2% stop loss.
   - **Max holding period**: e.g., `5` days.
4. Run the notebook to:
   - Apply the triple barrier labeling.
   - View trade labels (`+1`, `-1`, `0`) for each entry point.
   - Visualize the labeled trades.
  

## 5. Acknowledgements

- López de Prado, M. (2018). *Advances in Financial Machine Learning*. Wiley.



