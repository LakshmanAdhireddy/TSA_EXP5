Developed By : Lakshman 

Reg. NO . 212222240001

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
~~~python

# Importing the required libraries
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

# Load the dataset
  # Replace with the correct path to your file
df = pd.read_csv('india-gdp.csv')

# Display the first 5 rows of the dataset
print("First 5 Rows of the dataset:")
print(df.head())

# Converting the 'date' column to datetime and setting it as the index
df['date'] = pd.to_datetime(df['date'], format='%Y-%m-%d')
df.set_index('date', inplace=True)

# Filling missing values for the "tank" column (if any) using forward fill
df['AnnualChange'] = df['AnnualChange'].fillna(method='ffill')

# Performing seasonal decomposition on the "tank" feature (additive model)
decomposition = seasonal_decompose(df['AnnualChange'], model='additive', period=7)

# Plot and save each component separately with different colors

# Plot and save the observed (original) data
plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='blue')
plt.title('Observed')
plt.ylabel('Observed')
plt.savefig('observed_plot.png')
plt.show()

# Plot and save the trend component
plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='green')
plt.title('Trend')
plt.ylabel('Trend')
plt.savefig('trend_plot.png')
plt.show()

# Plot and save the seasonal component
plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='red')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.savefig('seasonal_plot.png')
plt.show()

# Plot and save the residual component
plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Residual')
plt.savefig('residual_plot.png')
plt.show()
~~~



### OUTPUT:
FIRST FIVE ROWS:

![172900081628321069657275375939](https://github.com/user-attachments/assets/68f31fa7-70c9-47b9-80a0-a9f40a12e326)


PLOTTING THE DATA:

![17290008840941068481349106028894](https://github.com/user-attachments/assets/8b2a83ae-fca6-4161-a953-75105eb7a685)


SEASONAL PLOT REPRESENTATION :

![172900084145087067771862023247](https://github.com/user-attachments/assets/802a4296-d4d6-4c68-9fbb-3c571c6bbb24)


TREND PLOT REPRESENTATION :

![17290008601168085361105575578385](https://github.com/user-attachments/assets/30ae424e-abb2-4ed9-a5d5-997227f89b9f)


OVERAL REPRESENTATION:
![17290009305263186835766082664177](https://github.com/user-attachments/assets/72fd3242-3b75-4c3c-a4e0-fd3d35d58751)



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
