## Developed by: Lakshman 

## Reg no:212222240001

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
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv('/content/KwhConsumptionBlower78_1.csv')
data.head()

data['TxnDate'] = pd.to_datetime(data['TxnDate'], errors='coerce')
data = data.dropna(subset=['TxnDate'])
data.set_index('TxnDate', inplace=True)

data['Consumption'] = pd.to_numeric(data['Consumption'], errors='coerce')

data = data.dropna(subset=['Consumption'])

plt.plot(data['Consumption'], label='Data')
plt.title('Plotting the Data')
plt.legend()
plt.show()

period = 13
result = seasonal_decompose(data['Consumption'], model='multiplicative', period=period)

plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.subplot(4, 1, 1)
plt.plot(data['Consumption'], label='original')
plt.title('Original Time Series')
plt.legend()
plt.show()

~~~


### OUTPUT:
FIRST FIVE ROWS:


![17290482711787519131572412686259](https://github.com/user-attachments/assets/432650d0-bcea-4b17-b08a-374aeda0c4db)

PLOTTING THE DATA:

![17290482834108399704249289755742](https://github.com/user-attachments/assets/053b2afc-6a42-4b34-b768-c8050ba17a6c)


SEASONAL PLOT REPRESENTATION :


![17290483066428638123502450289168](https://github.com/user-attachments/assets/735559ba-220f-4da2-9691-8490f1759644)


TREND PLOT REPRESENTATION :

![17290483302182315984279867320667](https://github.com/user-attachments/assets/040eb991-d881-488a-92bf-138bce94ba7c)


OVERAL REPRESENTATION:

![17290483432477648313862481650570](https://github.com/user-attachments/assets/82878997-b96e-4ef5-9d85-4d37f4f1ed10)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
