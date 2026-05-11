# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 11/05/2026


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
#Developed By: HAREESH R
#Reg No: 212223230068


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


gold_data = pd.read_csv("/content/AirPassengers.csv")


gold_data = gold_data.rename(columns={'Month': 'Date', '#Passengers': 'Price'})


gold_data['Date'] = pd.to_datetime(gold_data['Date'])

gold_data = gold_data.sort_values('Date')

gold_data.set_index('Date', inplace=True)

decomposition = seasonal_decompose(gold_data['Price'], model='additive', period=12)

plt.figure(figsize=(10, 12))

plt.subplot(411)
plt.plot(gold_data['Price'], label='Air Passengers')
plt.legend(loc='upper left')
plt.title('Air Passengers (1949–1960)')

plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```


### OUTPUT:

<img width="1052" height="570" alt="image" src="https://github.com/user-attachments/assets/7102ae15-4c97-4745-bfee-9436c646a236" />


<img width="1016" height="562" alt="image" src="https://github.com/user-attachments/assets/d5c52cc8-bec8-4a28-a6d1-8fbd16bb36a8" />



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
