### Name: GANESH R
### Reg.No: 212222240029
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### AIM:
To Illustrates how to perform time series analysis and decomposition on the Amazon Stock Price Dataset.

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

data = pd.read_csv('/content/Amazon.csv')
print("FIRST FIVE ROWS:")
print(data.head())
data = data.head(120)  # Adjust this number as per your dataset's requirement
data['Date'] = pd.date_range(start='1/1/2010', periods=len(data), freq='M')
data.set_index('Date', inplace=True)


result = seasonal_decompose(data['Volume'], model='additive', period=12) 
print("\nPLOTTING THE DATA:")
plt.figure(figsize=(10, 5))


plt.plot(data['Volume']) 
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
![image](https://github.com/user-attachments/assets/bd8a330c-bd74-4d37-b042-0d2af25827d7)
## PLOTTING THE DATA:
![image](https://github.com/user-attachments/assets/8cc35a8f-3b46-483e-a289-79596aa552df)
## SEASONAL PLOT REPRESENTATION:
![image](https://github.com/user-attachments/assets/4de28dc1-526f-47e2-861e-5dd6a566e328)
## TREND PLOT REPRESENTATION:
![image](https://github.com/user-attachments/assets/a6dcdd11-73b4-4312-946e-65b04d3412f4)
## OVERALL REPRESENTATION:
![image](https://github.com/user-attachments/assets/c0793ee4-8fdb-4a7f-a640-9cd93f6af5bd)

### RESULT:
Thus The python code has been created for the time series analysis and decomposition.
