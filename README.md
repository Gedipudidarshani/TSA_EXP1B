# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date:12-08-2025 
### NAME: GEDIPUDI DARSHANI
### REGISTER NUMBER:212223230062
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
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data=pd.read_csv('india.csv')
data.head()

data['date']=pd.to_datetime(data['date'])
data.set_index('date',inplace=True)
data['open_diff']=data['open']-data['open'].shift(1)

result = seasonal_decompose(data['open'], model='additive', period=12)
data['open_sea_diff']=result.resid

data['open_log'] = np.log(data['open'])
data['open_log_diff']=data['open_log']-data['open_log'].shift(1)

result = seasonal_decompose(data['open_log_diff'].dropna(), model='additive', period=12)
data['open_log_seasonal_diff']=result.resid

plt.figure(figsize=(16, 16))

plt.subplot(6, 1, 1)
plt.plot(data['open'], label='Original')
plt.legend(loc='best')
plt.title('Original Data')
plt.xlabel('date')
plt.ylabel('open')

plt.subplot(6, 1, 2)
plt.plot(data['open_diff'], label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')
plt.xlabel('date')
plt.ylabel('open')

plt.subplot(6, 1, 3)
plt.plot(data['open_sea_diff'], label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')
plt.xlabel('date')
plt.ylabel('open')

plt.subplot(6, 1, 4)
plt.plot(data['open_log'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.xlabel('Date')
plt.ylabel('Log(No of open)')

plt.subplot(6, 1, 5)
plt.plot(data['open_log_diff'], label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing')
plt.xlabel('Date')
plt.ylabel('RDiff(Log(No of open))')

plt.figure(figsize=(16, 16))
plt.subplot(6, 1, 6)
plt.plot(data['open_log_seasonal_diff'], label='Log Transformation and regular Differencing and Seasonal Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing and Seasonal Differencing')
plt.xlabel('Date')
plt.ylabel('SDiff(RDiff(Log(No of open)))')

plt.tight_layout()
plt.show()

data.plot(kind='line')
```

### OUTPUT:
ORIGINAL DATASET:
<img width="1452" height="320" alt="image" src="https://github.com/user-attachments/assets/b4cd62f9-aa5f-4eab-b494-1893878e1d99" />


REGULAR DIFFERENCING:
<img width="1451" height="326" alt="image" src="https://github.com/user-attachments/assets/7d0c232e-96f0-47c7-abd5-211e5d6e5855" />


SEASONAL ADJUSTMENT:
<img width="1446" height="330" alt="image" src="https://github.com/user-attachments/assets/d8df175b-bb43-49c4-a9a8-b11ef3e69807" />


LOG TRANSFORMATION:
<img width="1460" height="331" alt="image" src="https://github.com/user-attachments/assets/f4f49354-cb35-453b-b725-6e3b0e730453" />


<img width="1455" height="324" alt="image" src="https://github.com/user-attachments/assets/330f3a46-1cb8-4d24-8fe2-055a16e3bedd" />
<img width="1445" height="302" alt="image" src="https://github.com/user-attachments/assets/7c4b4e95-2050-43cf-bb4a-a590797d7168" />

OVERALL VIEW:
<img width="945" height="593" alt="image" src="https://github.com/user-attachments/assets/797c8f02-f4fc-49c0-a00e-be9f100e1ff2" />


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
