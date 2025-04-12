# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
### Date: 15/03/25

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
NAME : SWATHI D
REG NO. : 212222230154
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

data = pd.read_csv('rainfall.csv')

print("Column Names:", data.columns)

date_column = 'date'
humidity_column = 'humidity'

x = data[date_column]
y = data[humidity_column]

plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel(humidity_column)
plt.plot(x, y, label="Original Data")
plt.legend()
plt.show()

data['diff'] = data[humidity_column].diff()
data.dropna(inplace=True)

x = data[date_column]
y = data['diff']
plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel('Differenced Data')
plt.plot(x, y, label="Differenced Data", color='r')
plt.show()

data['SeasonalAdjustment'] = data[humidity_column] - data[humidity_column].rolling(window=12).mean()
data.dropna(inplace=True)

x = data[date_column]
y = data['SeasonalAdjustment']
plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel('Seasonally Adjusted Data')
plt.plot(x, y, label="Seasonal Adjustment", color='g')
plt.show()

data['log'] = np.log(data['diff'])
data.dropna(inplace=True)

x = data[date_column]
y = data['log']
plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel('Log Transformed Data')
plt.plot(x, y, label="Log Transformation", color='m')
plt.show()
```



### OUTPUT:

### ORIGINAL DATA:
![image](https://github.com/user-attachments/assets/e3ec87e1-e085-4927-bff4-261836846926)


### REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/f4d6639d-eed0-462c-9431-02a99811b135)



### SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/e8b953c7-0bc7-4f9b-a82c-5fb9eb91e649)


### LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/17984345-a337-4e1d-b95c-be0f8bae3b27)


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
