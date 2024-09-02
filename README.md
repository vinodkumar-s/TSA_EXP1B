### DEVELOPED BY: VINOD KUMAR S
### REGISTER NO: 212222240116
### DATE: 

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA


## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on coffee sales data.
## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
## PROGRAM:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

### Load the data
data = pd.read_csv('coffeesales.csv',nrows=100)

### Convert 'date' to datetime format
data['date'] = pd.to_datetime(data['date'])

### Group by date and calculate the average money spent per day
daily_average = data.groupby('date')['money'].mean().reset_index()

### Log transformation
daily_average['Log_Money'] = np.log(daily_average['money'])

### Regular differencing
daily_average['Diff_Log_Money'] = daily_average['Log_Money'].diff()

### Seasonal differencing (assuming daily data with weekly seasonality, period=7)
daily_average['Seasonal_Diff_Log_Money'] = daily_average['Log_Money'].diff(7)

### Plotting
plt.figure(figsize=(14, 12))

### Original data
plt.subplot(4, 1, 1)
plt.plot(daily_average['date'], daily_average['money'], label='Original')
plt.title('Original Data')
plt.ylabel('Average Money')
plt.grid()

### Log transformed data
plt.subplot(4, 1, 2)
plt.plot(daily_average['date'], daily_average['Log_Money'], label='Log Transformed', color='orange')
plt.title('Log Transformed Data')
plt.ylabel('Log(Average Money)')
plt.grid()

### Regular differenced data
plt.subplot(4, 1, 3)
plt.plot(daily_average['date'], daily_average['Diff_Log_Money'], label='Differenced', color='green')
plt.title('Differenced Log Data')
plt.ylabel('Diff(Log(Average Money))')
plt.grid()

### Seasonally differenced data
plt.subplot(4, 1, 4)
plt.plot(daily_average['date'], daily_average['Seasonal_Diff_Log_Money'], label='Seasonally Differenced', color='red')
plt.title('Seasonally Differenced Log Data')
plt.ylabel('Seasonal Diff(Log(Average Money))')
plt.grid()

plt.tight_layout()
plt.show()
```

## OUTPUT:

ORIGINAL DATA: 
![Screenshot 2024-08-23 221054](https://github.com/user-attachments/assets/26032487-b7da-4364-a92e-2d6544ba50c1)


REGULAR DIFFERENCING:

![Screenshot 2024-08-23 221132](https://github.com/user-attachments/assets/e54e6f21-a57a-4ce0-8963-77bb38de50d4)




SEASONAL ADJUSTMENT:

![Screenshot 2024-08-23 221146](https://github.com/user-attachments/assets/152bde13-91a0-41fb-b111-d96b242aeba3)



LOG TRANSFORMATION:

![Screenshot 2024-08-23 221118](https://github.com/user-attachments/assets/2c70c750-70e4-43fb-a25e-83427cadcdf1)



## RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on coffee sales data.
