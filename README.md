# Stock Price Simulation Using Monte Carlo Method

A Jupyter Notebook that simulates future stock prices using the **Monte Carlo method** combined with **Geometric Brownian Motion (GBM)**. Given a stock ticker, the model estimates the probability distribution of the stock's price at a future point in time based on its historical return and volatility.

---

## Overview

One of the key challenges investors face is evaluating the likelihood of future stock price movements. This notebook addresses that challenge by replicating price fluctuation stochastically using the Monte Carlo approach.

The workflow follows three main steps:

1. **Data Acquisition** — Fetch historical price data for a given ticker from [Stooq](https://stooq.com)
2. **Model Construction** — Estimate annual return (CAGR) and annualized volatility, then define the GBM equation
3. **Simulation & Analysis** — Run *N* simulations and analyze the resulting price distribution via percentiles

---

## Methodology

### Monte Carlo Simulation

The Monte Carlo method runs the GBM pricing function a large number of times (e.g. 1,000), each time drawing a different random shock from a standard normal distribution. This produces a distribution of possible future prices rather than a single point estimate.

### Geometric Brownian Motion (GBM)

The final stock price is calculated using the GBM equation from Reddy & Clinton (2016):

$$S_{t+\Delta t} = S_t \exp\left[\left(\mu - \frac{\hat{\sigma}^2}{2}\right)\Delta t + \hat{\sigma}\,\epsilon\sqrt{\Delta t}\right]$$

| Symbol | Description |
|--------|-------------|
| $S_t$ | Stock price at time $t$ |
| $S_{t+\Delta t}$ | Simulated future stock price |
| $\mu$ | Expected annual rate of return (CAGR) |
| $\hat{\sigma}$ | Annualized expected volatility |
| $\epsilon$ | Random draw from $\mathcal{N}(0, 1)$ |
| $\Delta t$ | Forecast horizon in years |

Annualized volatility is derived from the standard deviation of daily returns:

$$\hat{\sigma} = \frac{s}{\sqrt{\tau}}, \quad \tau = \frac{\Delta t}{N}$$

where $s$ is the standard deviation of daily returns and $N$ is the number of trading days in the look-back period.

---

## Requirements

```
numpy
pandas
scipy
seaborn
requests
python-dateutil
```

Install all dependencies with:

```bash
pip install numpy pandas scipy seaborn requests python-dateutil
```

---

## Configuration

At the top of the notebook, adjust the following parameters:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `ticker` | `'3175.HK'` | Stock ticker in [Stooq format](https://stooq.com) |
| `interval_prediction` | `1` | Forecast horizon in years |
| `number_of_simulations` | `1000` | Number of Monte Carlo runs |
| `look_back_x_years` | `5` | Historical look-back period in years |

---

## Usage

1. Clone or download the repository
2. Install the required dependencies
3. Open the notebook:
   ```bash
   jupyter notebook stock_price_simulation_using_monte_carlo_method.ipynb
   ```
4. Set your desired `ticker` and parameters in the configuration cell
5. Run all cells — the notebook will:
   - Download historical price data from Stooq
   - Plot the historical price series
   - Run the Monte Carlo simulation
   - Display a distribution plot of simulated prices
   - Print key percentiles of the simulated outcomes

### Example Output

After running the simulation, the notebook prints percentile values such as:

```
5 percentile:  <price>
25 percentile: <price>
50 percentile: <price>
75 percentile: <price>
95 percentile: <price>
```

These percentiles indicate the range of plausible future stock prices at the end of the forecast period.

---

## ⚠️ Disclaimer

The Monte Carlo model assumes that stock price movements follow a known probability distribution, which is a simplification. Real markets are subject to structural breaks, regime changes, and other non-random events. **Results should be interpreted with caution and are not financial advice.**

---

## References

Reddy, K. & Clinton, V. (2016). *Simulating Stock Prices Using Geometric Brownian Motion: Evidence from Australian Companies.* Australasian Accounting, Business and Finance Journal, 10(3), 23–47. [doi:10.14453/aabfj.v10i3.3](http://dx.doi.org/10.14453/aabfj.v10i3.3)
