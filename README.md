# DCS-Assignment--8
DCS-Assignment -8
#%%
import pandas as pd

# data frame

df = pd.DataFrame({'X': [7, 2, 0, 3, 4, 2, 5, 0, 3, 4]})

# extracting column as series
s = df.iloc[:,0]

# empty list
y = []
counter = 1

# calculating distance
for item in s:
    if(item==0):
      counter = 0
    y.append(counter)
    counter+=1

# adding to the data frame
df['Y'] = y

# check data frame
df

#%%
'''Create a DatetimeIndex that contains each business day of 2015 and use it to index a
Series of random numbers'''

import numpy as np
dti = pd.date_range(start='2015-01-01', end='2015-12-31', freq='B') 
s = pd.Series(np.random.rand(len(dti)), index=dti)
print(s[:10])

#%%
'''Find the sum of the values in s for every Wednesday.'''

sum = s[dti.weekday == 2].sum() 

print ("Sum of the values in s for every Wednesday = " + str (round(sum, 2)))

#%%
'''Average For each calendar month'''
s.resample('M', how='mean')
#%%
'''For each group of four consecutive calendar months in s, find the date on which the highest value occurred'''

s.groupby(pd.TimeGrouper('4M')).idxmax()

#%%
