# Portfolio Evolution Simulation using Monte Carlo

This Python script performs a Monte Carlo simulation to project the evolution of a stock portfolio over time. It uses historical stock data to estimate future portfolio values assuming a Brownian motion-like process. The script demonstrates a simplified model where the covariance of the stocks is assumed to be constant over time.

## Features

- Fetches historical closing prices of specified stocks using Yahoo Finance.
- Calculates daily returns, average returns, and covariance matrix for the selected stocks.
- Simulates future portfolio values using a Monte Carlo approach based on the historical data.
- Plots the simulated portfolio values over time.

## Prerequisites

Before you run the script, ensure you have Python installed along with the following packages:
- `pandas`
- `numpy`
- `matplotlib`
- `pandas_datareader`
- `scipy`
- `yfinance`

You can install these packages using pip:

```bash
pip install pandas numpy matplotlib pandas_datareader scipy yfinance
```

## Usage

To run the simulation, follow these steps:

1. **Modify the Stock List:** Edit the `stockList` variable in the script to include the ticker symbols of the stocks you want to include in your portfolio.
2. **Adjust the Time Frame:** Set the `startDate` and `endDate` to define the historical data period for the simulation.
3. **Set the Simulation Parameters:** Adjust `mc_sims` for the number of simulations and `T` for the number of days to simulate into the future.
4. **Run the Script:** Execute the script in your Python environment. The resulting plot will display the simulated trajectories of the portfolio value over the specified period.

## Example

Here is a brief section of the code for quick reference:

```python
# Define stock list and date range
stockList = ['CBA', 'BHP', 'TLS', 'NAB', 'WBC', 'STO']
stocks = [stock + '.AX' for stock in stockList]
endDate = dt.datetime.now()
startDate = endDate - dt.timedelta(days=800)

# Fetch data and perform Monte Carlo simulation
returns, meanReturns, covMatrix = getData(stocks, start=startDate, end=endDate)
weights = np.random.rand(len(meanReturns))
weights /= sum(weights)
portfolio_sims = monteCarloSimulation(returns, meanReturns, covMatrix, weights)
```

## Output

The script will output a plot showing the potential evolution of the portfolio value over the specified time frame, illustrating the variability expected due to the stochastic nature of stock returns.

## Acknowledgements

This script is adapted from a tutorial by [YouTube Channel](https://www.youtube.com/watch?v=6-dhdMDiYWQ). All rights and credits for the original concept and portions of the code belong to them.
