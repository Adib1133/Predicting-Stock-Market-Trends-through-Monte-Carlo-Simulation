Stock Price Simulation Using Monte Carlo Method

Overview:
This project uses the **Monte Carlo Method** to simulate stock price movements in this case, the stock market prices of Samsung inc has been taken as an example. The Monte Carlo approach assumes that stock price behavior follows a probability distribution, allowing it to model and predict potential future prices. The datasets has been taken from Yahoo finance and stook. 

Motivation:
One of the biggest challenges investors face is estimating the likelihood of stock price changes and predicting whether a stock will reach a specific value. This project aims to:
- Simulate stock price movements using **Geometric Brownian Motion (GBM)**.
- Provide insights into potential price fluctuations based on historical data.
- Run multiple simulations to observe price variations over time.

Methodology:
1. **Data Collection**: The model uses **5 years of historical stock data** to estimate key parameters such as expected annual return and volatility.
2. **Model Creation**: Stock price movements are simulated using **Geometric Brownian Motion (GBM)**.
3. **Simulation Execution**: The Monte Carlo method runs multiple simulations (e.g., **1,000 simulations**) to project future stock prices.
4. **Visualization**: The simulated price paths are plotted to visualize potential stock price movements.

Technologies Used:
 **Python**  
 **NumPy**  
 **Pandas**  
 **Seaborn**  
 **SciPy**  
 **Matplotlib**  

Results:
Multiple stock price simulations are generated to show potential future price paths. The results provide insights into possible price ranges and volatility.

Limitations:
Assumes stock price movements follow Geometric Brownian Motion (GBM).
Does not account for market events, news, or sudden economic changes.
Results should be interpreted carefully and not considered financial advice.
