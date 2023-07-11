# Stock_Market_Time_Series_Prediction
 Stock market prediction using time series analysis.
Create stock price predictions using an LSTM (Long Short-Term Memory) model:

1. Importing the required libraries:
   - `yfinance` (imported as `yf`) is used to download historical stock price data.
   - `numpy` (imported as `np`) is used for numerical operations.
   - `pandas` (imported as `pd`) is used for data manipulation.
   - `MinMaxScaler` from `sklearn.preprocessing` is used to scale the data.
   - `Sequential` and `LSTM` from `tensorflow.keras.models` and `tensorflow.keras.layers` are used to build the LSTM model.
   - `matplotlib.pyplot` (imported as `plt`) is used for data visualization.

2. `create_stock_prediction` function:
   - This function takes three arguments: `ticker` (the stock ticker symbol), `n` (the number of future predictions to make), and `train_size` (the proportion of data to use for training, default is 0.9).
   - The function first downloads the historical stock price data using `yf.download` and stores it in the `data` variable.
   - The data is then prepared for the LSTM model by extracting the "Close" prices and reshaping them into a column vector.
   - The data is scaled using `MinMaxScaler` to ensure all values are between 0 and 1.
   - The scaled data is split into training and testing sets based on the `train_size` parameter.
   - Next, the function defines a nested function `create_sequences` that creates input sequences and corresponding labels for training the LSTM model.
   - The function builds the LSTM model using `Sequential` and adds two LSTM layers and a dense layer with a single output.
   - The model is compiled with the Adam optimizer and mean squared error loss.
   - The model is trained using the training data for the specified number of epochs and batch size.
   - After training, the model makes predictions on the test data.
   - The predictions and actual values are inverse scaled to obtain the original stock price values.
   - The mean squared error (MSE) between the predictions and actual values is calculated and printed.
   - The predictions and actual values are converted to pandas DataFrames with dates as the index.
   - A nested function `plot_predictions` is defined to visualize the predictions and actual values.
   - The function plots the actual values, predictions for the available data, and future predictions beyond the available data.
   - The next `n` predicted values are printed as a DataFrame.
   - Finally, the `plot_predictions` function is called to visualize the predictions and the next `n` predicted values are printed.

3. Example usage:
   - The `create_stock_prediction` function is called multiple times with different stock tickers ("AAPL", "MSFT", "AMZN") and `n` value (15) to demonstrate how to use the function and generate stock price predictions.
