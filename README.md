### DEVELOPED BY: Nivetha A

### REGISTER NUMBER: 212222230101

### Date:


# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
 


### AIM:
To perform time series analysis and decomposition on monthly average data of a digital currency (USD closing prices) using the multiplicative decomposition model, and visualize its trend, seasonality, and residual components.

### ALGORITHM:

   1. Import the required libraries: pandas, matplotlib, and seasonal_decompose from statsmodels.
  
   2. Load the dataset and parse the date column as the index.
   
   3. Resample the data by month, calculating the mean of the closing price (close_USD).
  
   4. Perform time series decomposition using a multiplicative model.
   
   5.  Plot the decomposition showing observed, trend, seasonal, and residual components.
   
   6. Set the x-axis to display only the starting year using YearLocator and DateFormatter.
   
   7. Rotate the x-axis labels for better readability.
   
   8. Display the plot with adjusted font sizes for clarity.


### PROGRAM:
```
## Import the required libraries
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.dates as mdates

## Load the dataset from the uploaded file
file_path = 'digital_currency.csv'
data = pd.read_csv(file_path)

## Parse the 'Unnamed: 0' column as dates and set it as the index
data['Date'] = pd.to_datetime(data['Unnamed: 0'])
data.set_index('Date', inplace=True)

## Resample the data to monthly frequency using the mean of 'close_USD'
monthly_data = data['close_USD'].resample('M').mean()

## Perform seasonal decomposition
decomposition = seasonal_decompose(monthly_data, model='multiplicative', period=12)

## Plot the decomposition results
fig = decomposition.plot()

## Access the axes of the plots
for ax in fig.axes:
    # Set the x-axis to display only the year at the start of each year
    ax.xaxis.set_major_locator(mdates.YearLocator())  # Set major ticks at the start of each year
    ax.xaxis.set_major_formatter(mdates.DateFormatter('%Y'))  # Format the ticks to display only the year

    # Improve the tick label visibility
    ax.tick_params(axis='x', rotation=45)  # Rotate x-axis labels for better readability

## Set font sizes for better clarity on axis labels and ticks
plt.rc('axes', titlesize=14)   # Titles
plt.rc('axes', labelsize=12)   # Axes labels
plt.rc('xtick', labelsize=10)  # X-tick labels
plt.rc('ytick', labelsize=10)  # Y-tick labels
plt.rc('legend', fontsize=12)  # Legend font size

plt.tight_layout()
plt.show()
```

### OUTPUT:

![369756525-99619216-98e9-439f-aebd-06f8fb6f4455](https://github.com/user-attachments/assets/2959998a-12cd-4ab2-b712-123b6a0d719a)



### RESULT:
Thus, the python code for time series decomposition was successfully performed on the monthly average close_USD prices of the digital currency.
