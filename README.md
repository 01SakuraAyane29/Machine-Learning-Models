# Machine-Learning-Models
I did a house price calculator in my project.<br>
I used Colab to train my models and see runtime outputs.<br>
All the outputs including the graphs and logs are displayed below the code section.<br>
The last model in the `DecisionTrees` file is the final model I used in my project.<br>

## Preparing the data
```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy as sp
import sklearn as sk
import time
import datetime

data = pd.read_csv('kc_house_data.csv',sep=',')
y_data = data['price']
x_data = data.drop(columns = ['id','date','price'])

date = data['date']

date = date.apply(lambda x: time.strptime(x[2:4]+x[4:6]+x[6:8], '%y%m%d'))

date = date.apply(lambda x: (time.mktime(datetime.datetime.now().timetuple())
                             -time.mktime(x))/86400)

x_data.insert(1,'date',date)
```
## Visualising the data
