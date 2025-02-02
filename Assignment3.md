# Assignment 3


```python
## Import modules first
import pandas as pd
import matplotlib.pyplot as plot
from datetime import datetime

%matplotlib inline

#import csv file and load it into a dataframe
data_file = 'data/atlantic.csv'
data = pd.read_csv(data_file)
```

### How does the data look like?

There are 49105 rows of data. Each row has 22 columns.


```python
#get a statistcal summary of the data
data.describe().round(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Time</th>
      <th>Maximum Wind</th>
      <th>Minimum Pressure</th>
      <th>Low Wind NE</th>
      <th>Low Wind SE</th>
      <th>Low Wind SW</th>
      <th>Low Wind NW</th>
      <th>Moderate Wind NE</th>
      <th>Moderate Wind SE</th>
      <th>Moderate Wind SW</th>
      <th>Moderate Wind NW</th>
      <th>High Wind NE</th>
      <th>High Wind SE</th>
      <th>High Wind SW</th>
      <th>High Wind NW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
      <td>49105.00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>19498020.10</td>
      <td>910.13</td>
      <td>52.01</td>
      <td>-251.41</td>
      <td>-868.67</td>
      <td>-869.32</td>
      <td>-872.68</td>
      <td>-871.41</td>
      <td>-875.57</td>
      <td>-875.77</td>
      <td>-876.68</td>
      <td>-876.32</td>
      <td>-877.56</td>
      <td>-877.66</td>
      <td>-877.92</td>
      <td>-877.79</td>
    </tr>
    <tr>
      <th>std</th>
      <td>446185.05</td>
      <td>671.04</td>
      <td>27.68</td>
      <td>964.31</td>
      <td>353.30</td>
      <td>351.55</td>
      <td>342.15</td>
      <td>345.63</td>
      <td>333.65</td>
      <td>333.13</td>
      <td>330.53</td>
      <td>331.54</td>
      <td>328.03</td>
      <td>327.77</td>
      <td>327.02</td>
      <td>327.41</td>
    </tr>
    <tr>
      <th>min</th>
      <td>18510625.00</td>
      <td>0.00</td>
      <td>-99.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>19111101.00</td>
      <td>600.00</td>
      <td>35.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>19560927.00</td>
      <td>1200.00</td>
      <td>45.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>19890810.00</td>
      <td>1800.00</td>
      <td>70.00</td>
      <td>990.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
      <td>-999.00</td>
    </tr>
    <tr>
      <th>max</th>
      <td>20151113.00</td>
      <td>2330.00</td>
      <td>165.00</td>
      <td>1024.00</td>
      <td>710.00</td>
      <td>600.00</td>
      <td>640.00</td>
      <td>530.00</td>
      <td>360.00</td>
      <td>300.00</td>
      <td>330.00</td>
      <td>360.00</td>
      <td>180.00</td>
      <td>250.00</td>
      <td>150.00</td>
      <td>180.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
#check how the first 10 records of the data dataframe look like
data.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Date</th>
      <th>Time</th>
      <th>Event</th>
      <th>Status</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Maximum Wind</th>
      <th>Minimum Pressure</th>
      <th>...</th>
      <th>Low Wind SW</th>
      <th>Low Wind NW</th>
      <th>Moderate Wind NE</th>
      <th>Moderate Wind SE</th>
      <th>Moderate Wind SW</th>
      <th>Moderate Wind NW</th>
      <th>High Wind NE</th>
      <th>High Wind SE</th>
      <th>High Wind SW</th>
      <th>High Wind NW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>0</td>
      <td></td>
      <td>HU</td>
      <td>28.0N</td>
      <td>94.8W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>600</td>
      <td></td>
      <td>HU</td>
      <td>28.0N</td>
      <td>95.4W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>1200</td>
      <td></td>
      <td>HU</td>
      <td>28.0N</td>
      <td>96.0W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>1800</td>
      <td></td>
      <td>HU</td>
      <td>28.1N</td>
      <td>96.5W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>2100</td>
      <td>L</td>
      <td>HU</td>
      <td>28.2N</td>
      <td>96.8W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>5</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510626</td>
      <td>0</td>
      <td></td>
      <td>HU</td>
      <td>28.2N</td>
      <td>97.0W</td>
      <td>70</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>6</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510626</td>
      <td>600</td>
      <td></td>
      <td>TS</td>
      <td>28.3N</td>
      <td>97.6W</td>
      <td>60</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>7</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510626</td>
      <td>1200</td>
      <td></td>
      <td>TS</td>
      <td>28.4N</td>
      <td>98.3W</td>
      <td>60</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>8</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510626</td>
      <td>1800</td>
      <td></td>
      <td>TS</td>
      <td>28.6N</td>
      <td>98.9W</td>
      <td>50</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>9</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510627</td>
      <td>0</td>
      <td></td>
      <td>TS</td>
      <td>29.0N</td>
      <td>99.4W</td>
      <td>50</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
  </tbody>
</table>
<p>10 rows × 22 columns</p>
</div>




```python
# which rows are null for any of the columns?
data[data.isna().any(axis=1)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Date</th>
      <th>Time</th>
      <th>Event</th>
      <th>Status</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Maximum Wind</th>
      <th>Minimum Pressure</th>
      <th>...</th>
      <th>Low Wind SW</th>
      <th>Low Wind NW</th>
      <th>Moderate Wind NE</th>
      <th>Moderate Wind SE</th>
      <th>Moderate Wind SW</th>
      <th>Moderate Wind NW</th>
      <th>High Wind NE</th>
      <th>High Wind SE</th>
      <th>High Wind SW</th>
      <th>High Wind NW</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
<p>0 rows × 22 columns</p>
</div>




```python
# since the explanatory notes of the dataset says that "-999" is used as a placeholder value for fields that have no data.
# Let's see how many rows have '-999' in any one of the columns.
data[(data == -999).any(axis=1)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Date</th>
      <th>Time</th>
      <th>Event</th>
      <th>Status</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Maximum Wind</th>
      <th>Minimum Pressure</th>
      <th>...</th>
      <th>Low Wind SW</th>
      <th>Low Wind NW</th>
      <th>Moderate Wind NE</th>
      <th>Moderate Wind SE</th>
      <th>Moderate Wind SW</th>
      <th>Moderate Wind NW</th>
      <th>High Wind NE</th>
      <th>High Wind SE</th>
      <th>High Wind SW</th>
      <th>High Wind NW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>0</td>
      <td></td>
      <td>HU</td>
      <td>28.0N</td>
      <td>94.8W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>600</td>
      <td></td>
      <td>HU</td>
      <td>28.0N</td>
      <td>95.4W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>1200</td>
      <td></td>
      <td>HU</td>
      <td>28.0N</td>
      <td>96.0W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>1800</td>
      <td></td>
      <td>HU</td>
      <td>28.1N</td>
      <td>96.5W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AL011851</td>
      <td>UNNAMED</td>
      <td>18510625</td>
      <td>2100</td>
      <td>L</td>
      <td>HU</td>
      <td>28.2N</td>
      <td>96.8W</td>
      <td>80</td>
      <td>-999</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>47043</th>
      <td>AL082011</td>
      <td>HARVEY</td>
      <td>20110820</td>
      <td>1730</td>
      <td>L</td>
      <td>TS</td>
      <td>17.0N</td>
      <td>88.3W</td>
      <td>55</td>
      <td>995</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>47057</th>
      <td>AL092011</td>
      <td>IRENE</td>
      <td>20110821</td>
      <td>2300</td>
      <td>L</td>
      <td>TS</td>
      <td>17.8N</td>
      <td>64.6W</td>
      <td>60</td>
      <td>993</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>47059</th>
      <td>AL092011</td>
      <td>IRENE</td>
      <td>20110822</td>
      <td>525</td>
      <td>L</td>
      <td>TS</td>
      <td>18.1N</td>
      <td>65.8W</td>
      <td>60</td>
      <td>990</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>47070</th>
      <td>AL092011</td>
      <td>IRENE</td>
      <td>20110824</td>
      <td>1600</td>
      <td>L</td>
      <td>HU</td>
      <td>22.4N</td>
      <td>74.0W</td>
      <td>100</td>
      <td>955</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
    <tr>
      <th>47074</th>
      <td>AL092011</td>
      <td>IRENE</td>
      <td>20110825</td>
      <td>900</td>
      <td>L</td>
      <td>HU</td>
      <td>24.7N</td>
      <td>76.2W</td>
      <td>90</td>
      <td>950</td>
      <td>...</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
      <td>-999</td>
    </tr>
  </tbody>
</table>
<p>43184 rows × 22 columns</p>
</div>




```python
# show the rows that don't have '-999'
data[~(data == -999).any(axis=1)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Date</th>
      <th>Time</th>
      <th>Event</th>
      <th>Status</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Maximum Wind</th>
      <th>Minimum Pressure</th>
      <th>...</th>
      <th>Low Wind SW</th>
      <th>Low Wind NW</th>
      <th>Moderate Wind NE</th>
      <th>Moderate Wind SE</th>
      <th>Moderate Wind SW</th>
      <th>Moderate Wind NW</th>
      <th>High Wind NE</th>
      <th>High Wind SE</th>
      <th>High Wind SW</th>
      <th>High Wind NW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>43104</th>
      <td>AL012004</td>
      <td>ALEX</td>
      <td>20040731</td>
      <td>1800</td>
      <td></td>
      <td>TD</td>
      <td>30.3N</td>
      <td>78.3W</td>
      <td>25</td>
      <td>1010</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43105</th>
      <td>AL012004</td>
      <td>ALEX</td>
      <td>20040801</td>
      <td>0</td>
      <td></td>
      <td>TD</td>
      <td>31.0N</td>
      <td>78.8W</td>
      <td>25</td>
      <td>1009</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43106</th>
      <td>AL012004</td>
      <td>ALEX</td>
      <td>20040801</td>
      <td>600</td>
      <td></td>
      <td>TD</td>
      <td>31.5N</td>
      <td>79.0W</td>
      <td>25</td>
      <td>1009</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43107</th>
      <td>AL012004</td>
      <td>ALEX</td>
      <td>20040801</td>
      <td>1200</td>
      <td></td>
      <td>TD</td>
      <td>31.6N</td>
      <td>79.1W</td>
      <td>30</td>
      <td>1009</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>43108</th>
      <td>AL012004</td>
      <td>ALEX</td>
      <td>20040801</td>
      <td>1800</td>
      <td></td>
      <td>TS</td>
      <td>31.6N</td>
      <td>79.2W</td>
      <td>35</td>
      <td>1009</td>
      <td>...</td>
      <td>50</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>49100</th>
      <td>AL122015</td>
      <td>KATE</td>
      <td>20151112</td>
      <td>1200</td>
      <td></td>
      <td>EX</td>
      <td>41.3N</td>
      <td>50.4W</td>
      <td>55</td>
      <td>981</td>
      <td>...</td>
      <td>180</td>
      <td>120</td>
      <td>120</td>
      <td>120</td>
      <td>60</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>49101</th>
      <td>AL122015</td>
      <td>KATE</td>
      <td>20151112</td>
      <td>1800</td>
      <td></td>
      <td>EX</td>
      <td>41.9N</td>
      <td>49.9W</td>
      <td>55</td>
      <td>983</td>
      <td>...</td>
      <td>180</td>
      <td>120</td>
      <td>120</td>
      <td>120</td>
      <td>60</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>49102</th>
      <td>AL122015</td>
      <td>KATE</td>
      <td>20151113</td>
      <td>0</td>
      <td></td>
      <td>EX</td>
      <td>41.5N</td>
      <td>49.2W</td>
      <td>50</td>
      <td>985</td>
      <td>...</td>
      <td>200</td>
      <td>220</td>
      <td>120</td>
      <td>120</td>
      <td>60</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>49103</th>
      <td>AL122015</td>
      <td>KATE</td>
      <td>20151113</td>
      <td>600</td>
      <td></td>
      <td>EX</td>
      <td>40.8N</td>
      <td>47.5W</td>
      <td>45</td>
      <td>985</td>
      <td>...</td>
      <td>180</td>
      <td>220</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>49104</th>
      <td>AL122015</td>
      <td>KATE</td>
      <td>20151113</td>
      <td>1200</td>
      <td></td>
      <td>EX</td>
      <td>40.7N</td>
      <td>45.4W</td>
      <td>45</td>
      <td>987</td>
      <td>...</td>
      <td>150</td>
      <td>220</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5921 rows × 22 columns</p>
</div>



#### Create some graphs!


```python
# The use of '-999' as a placeholder value has great ramifications as to future data cleaning.
# It's useful to see how much of the data is littered with -999. The results will be shown in a pie chart.

# Identify rows with any -999
has_negative_999 = (data == -999).any(axis=1)

# Count rows with and without -999
counts = has_negative_999.value_counts()

# Prepare data for the pie chart
labels = ['Rows with -999', 'Rows without -999']
sizes = [counts[True] if True in counts else 0, counts[False] if False in counts else 0]
colors = ['#FF9999', '#99FF99']

# Create pie chart
plot.figure(figsize=(8, 8))
plot.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%', startangle=140, wedgeprops={'edgecolor': 'black'})

plot.title('Distribution of Rows with and without -999')
plot.axis('equal')  # Equal aspect ratio to make the pie circular
plot.show()
```


    
![png](output_9_0.png)
    



```python
# Although there are 49105 rows of data. It doesn't mean that there were 49105 storms on record.
# We can count how many storms are recorded based on 'ID'.
print ("There are " + str(data['ID'].nunique()) + " storms in the dataset.")
```

    There are 1814 storms in the dataset.
    


```python
# We can look at the peak intensity of the 1814 storms.
# Peak intensity is defined by the highest maximum wind speed recorded for the storm.

# Get the row where "Maximum Wind" is highest for each unique "ID"
filtered_data = data.loc[data.groupby("ID")["Maximum Wind"].idxmax()]

# Count occurrences of "Status" in the filtered dataset
status_counts = filtered_data["Status"].value_counts()

# Plot the counts
plot.figure(figsize=(12, 6))
status_counts.plot(kind='bar', color='orange', edgecolor="black")
plot.title("Storm Intensity (Peak Intensity)")
plot.xlabel("Storm Type")
plot.ylabel("Count")
plot.grid(axis='y')
plot.xticks(rotation=0)
plot.show()

```


    
![png](output_11_0.png)
    



```python
# 12 attributes in the data are dedicated to record how strong the wind is from the eye.
# 3 thresholds are established for each quadrant, i.e. the Northeast, Northwest, Southeast and Southwest.
# The thresholds are, 34 kts - low, 50 kts - moderate, 64 kts - high.
# The number represents how many nautical miles from the eye did the wind reach the threshold.
# The plot below looks at the high winds, and identify the largest number in the attribute.

# Find the maximum value for each wind quadrant
max_values = data[['High Wind NE', 'High Wind NW', 'High Wind SE', 'High Wind SW']].max()

# Create the bar chart
plot.figure(figsize=(10, 6))
max_values.plot(kind='bar', color='royalblue', edgecolor='black')

# Labels and title
plot.xlabel("Wind Quadrant")
plot.ylabel("Maximum Extent (nautical miles)")
plot.title("Maximum Wind Radii in Each Quadrant")
plot.xticks(rotation=45)

# Show the values on top of bars
for i, v in enumerate(max_values):
    plot.text(i, v + 5, str(v), ha='center', fontsize=12, fontweight='bold')

# Display the chart
plot.show()
```


    
![png](output_12_0.png)
    


#### What does the dataset tell you?

This dataset records historical cyclone data from the Atlantic Basin between 1851 and 2014. It contains 49,105 records with 22 columns, capturing details of individual storm observations. Here’s what you need to know:
##### Key Columns and Their Meanings:
*ID*: A unique identifier for each storm (e.g., "AL011851" represents the first storm of 1851).

*Name*: The name of the cyclone (many older storms are unnamed).

*Date & Time*: When the observation was recorded (format: YYYYMMDD for date, HHMM for time).

*Event*: A marker for specific storm events (e.g., landfall).

*Status*: The storm classification (e.g., HU = Hurricane, TS = Tropical Storm).

*Latitude & Longitude*: The storm's location at the recorded time.

*Maximum Wind*: The highest recorded wind speed in knots.

*Minimum Pressure*: The lowest atmospheric pressure recorded in millibars (negative values like "-999" indicate missing data).

*Wind Radius*: The extent of wind speeds (low, moderate, and high) in different quadrants (NE, SE, SW, NW).

##### What You Can Learn from This Dataset:
How storms track across the Atlantic over time.

Changes in cyclone frequency and intensity over the years.

Geographic areas most affected by strong storms.


```python

```
