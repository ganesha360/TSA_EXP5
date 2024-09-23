### Name: KARTHIKEYAN R
### Reg.No: 212222240046
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### AIM:
To Illustrates how to perform time series analysis and decomposition on the Gold price Dataset.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv('/content/Gold Price.csv')
print("FIRST FIVE ROWS:")
print(data.head())
data = data.head(120)  # Adjust this number as per your dataset's requirement
data['Date'] = pd.date_range(start='1/1/2010', periods=len(data), freq='M')
data.set_index('Date', inplace=True)
# The 'Price' column is used here instead of 'Temperature'
result = seasonal_decompose(data['Price'], model='additive', period=12) 
print("\nPLOTTING THE DATA:")
plt.figure(figsize=(10, 5))
# The 'Price' column is used here instead of 'Temperature'
plt.plot(data['Price']) 
plt.title('Yearly Average price Over Time')
plt.xlabel('Year')
plt.ylabel('Price')
plt.show()
print("\nSEASONAL PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.seasonal.plot()
plt.title('Seasonal Decomposition')
plt.ylabel('Seasonal Component')
plt.show()
print("\nTREND PLOT REPRESENTATION:")
plt.figure(figsize=(10, 5))
result.trend.plot()
plt.title('Trend Decomposition')
plt.ylabel('Trend Component')
plt.show()
print("\nOVERALL REPRESENTATION:")
fig, (ax1, ax2, ax3, ax4) = plt.subplots(4, 1, figsize=(10, 10))
result.observed.plot(ax=ax1)
ax1.set_ylabel('Observed')
result.trend.plot(ax=ax2)
ax2.set_ylabel('Trend')
result.seasonal.plot(ax=ax3)
ax3.set_ylabel('Seasonal')
result.resid.plot(ax=ax4)
ax4.set_ylabel('Residual')
plt.tight_layout()
plt.show()
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/94c0f1b8-86c2-4b8f-bdb4-5fbb74f41132)
![image](https://github.com/user-attachments/assets/b447ea51-08a0-4141-b9c0-16eb05cda742)
![image](https://github.com/user-attachments/assets/b4e0f71c-311e-439e-afa5-93e9a9bfae12)
![image](https://github.com/user-attachments/assets/19739e83-9097-4b3b-ab47-3913d2a0c8a2)
![image](https://github.com/user-attachments/assets/2d0b5efd-1a27-4b65-9111-190b5d31f341)

### RESULT:
Thus The python code has been created for the time series analysis and decomposition.
