```python
import pandas as pd
df=pd.read_csv('../data/gapminder.tsv', sep='\t')
```


```python
print(df)
```

              country continent  year  lifeExp       pop   gdpPercap
    0     Afghanistan      Asia  1952   28.801   8425333  779.445314
    1     Afghanistan      Asia  1957   30.332   9240934  820.853030
    2     Afghanistan      Asia  1962   31.997  10267083  853.100710
    3     Afghanistan      Asia  1967   34.020  11537966  836.197138
    4     Afghanistan      Asia  1972   36.088  13079460  739.981106
    ...           ...       ...   ...      ...       ...         ...
    1699     Zimbabwe    Africa  1987   62.351   9216418  706.157306
    1700     Zimbabwe    Africa  1992   60.377  10704340  693.420786
    1701     Zimbabwe    Africa  1997   46.809  11404948  792.449960
    1702     Zimbabwe    Africa  2002   39.989  11926563  672.038623
    1703     Zimbabwe    Africa  2007   43.487  12311143  469.709298
    
    [1704 rows x 6 columns]
    


```python
df.shape
```




    (1704, 6)




```python
type(df)
```




    pandas.core.frame.DataFrame




```python
df.columns
```




    Index(['country', 'continent', 'year', 'lifeExp', 'pop', 'gdpPercap'], dtype='object')




```python
df.dtypes
```




    country       object
    continent     object
    year           int64
    lifeExp      float64
    pop            int64
    gdpPercap    float64
    dtype: object




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1704 entries, 0 to 1703
    Data columns (total 6 columns):
     #   Column     Non-Null Count  Dtype  
    ---  ------     --------------  -----  
     0   country    1704 non-null   object 
     1   continent  1704 non-null   object 
     2   year       1704 non-null   int64  
     3   lifeExp    1704 non-null   float64
     4   pop        1704 non-null   int64  
     5   gdpPercap  1704 non-null   float64
    dtypes: float64(2), int64(2), object(2)
    memory usage: 80.0+ KB
    


```python
df.head()
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
      <th>country</th>
      <th>continent</th>
      <th>year</th>
      <th>lifeExp</th>
      <th>pop</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1952</td>
      <td>28.801</td>
      <td>8425333</td>
      <td>779.445314</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1957</td>
      <td>30.332</td>
      <td>9240934</td>
      <td>820.853030</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1962</td>
      <td>31.997</td>
      <td>10267083</td>
      <td>853.100710</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1967</td>
      <td>34.020</td>
      <td>11537966</td>
      <td>836.197138</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1972</td>
      <td>36.088</td>
      <td>13079460</td>
      <td>739.981106</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['country']
```




    0       Afghanistan
    1       Afghanistan
    2       Afghanistan
    3       Afghanistan
    4       Afghanistan
               ...     
    1699       Zimbabwe
    1700       Zimbabwe
    1701       Zimbabwe
    1702       Zimbabwe
    1703       Zimbabwe
    Name: country, Length: 1704, dtype: object




```python
subset=df[['country','year','pop']]
print(subset)
```

              country  year       pop
    0     Afghanistan  1952   8425333
    1     Afghanistan  1957   9240934
    2     Afghanistan  1962  10267083
    3     Afghanistan  1967  11537966
    4     Afghanistan  1972  13079460
    ...           ...   ...       ...
    1699     Zimbabwe  1987   9216418
    1700     Zimbabwe  1992  10704340
    1701     Zimbabwe  1997  11404948
    1702     Zimbabwe  2002  11926563
    1703     Zimbabwe  2007  12311143
    
    [1704 rows x 3 columns]
    


```python
type(subset)
```




    pandas.core.frame.DataFrame




```python
df['country']

```




    0       Afghanistan
    1       Afghanistan
    2       Afghanistan
    3       Afghanistan
    4       Afghanistan
               ...     
    1699       Zimbabwe
    1700       Zimbabwe
    1701       Zimbabwe
    1702       Zimbabwe
    1703       Zimbabwe
    Name: country, Length: 1704, dtype: object




```python
df.loc[0]
type(df.loc[0])
```




    pandas.core.series.Series




```python
df.iloc[0]
```




    country      Afghanistan
    continent           Asia
    year                1952
    lifeExp           28.801
    pop              8425333
    gdpPercap     779.445314
    Name: 0, dtype: object




```python
#df.loc[-1]  #불가능 
df.iloc[-1] #loc는 이릅값으로 참조하지만, iloc는 번호로 참조
```




    country        Zimbabwe
    continent        Africa
    year               2007
    lifeExp          43.487
    pop            12311143
    gdpPercap    469.709298
    Name: 1703, dtype: object




```python
df.iloc[100]
```




    country      Bangladesh
    continent          Asia
    year               1972
    lifeExp          45.252
    pop            70759295
    gdpPercap    630.233627
    Name: 100, dtype: object




```python
df.loc[[0,99]]
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
      <th>country</th>
      <th>continent</th>
      <th>year</th>
      <th>lifeExp</th>
      <th>pop</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1952</td>
      <td>28.801</td>
      <td>8425333</td>
      <td>779.445314</td>
    </tr>
    <tr>
      <th>99</th>
      <td>Bangladesh</td>
      <td>Asia</td>
      <td>1967</td>
      <td>43.453</td>
      <td>62821884</td>
      <td>721.186086</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(df.loc[0:4])
print(df.iloc[0:4])  #차이 주의

```

           country continent  year  lifeExp       pop   gdpPercap
    0  Afghanistan      Asia  1952   28.801   8425333  779.445314
    1  Afghanistan      Asia  1957   30.332   9240934  820.853030
    2  Afghanistan      Asia  1962   31.997  10267083  853.100710
    3  Afghanistan      Asia  1967   34.020  11537966  836.197138
    4  Afghanistan      Asia  1972   36.088  13079460  739.981106
           country continent  year  lifeExp       pop   gdpPercap
    0  Afghanistan      Asia  1952   28.801   8425333  779.445314
    1  Afghanistan      Asia  1957   30.332   9240934  820.853030
    2  Afghanistan      Asia  1962   31.997  10267083  853.100710
    3  Afghanistan      Asia  1967   34.020  11537966  836.197138
    


```python
df.iloc[[0,2,3]]
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
      <th>country</th>
      <th>continent</th>
      <th>year</th>
      <th>lifeExp</th>
      <th>pop</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1952</td>
      <td>28.801</td>
      <td>8425333</td>
      <td>779.445314</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1962</td>
      <td>31.997</td>
      <td>10267083</td>
      <td>853.100710</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1967</td>
      <td>34.020</td>
      <td>11537966</td>
      <td>836.197138</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[:,[1,3,-1]]
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
      <th>continent</th>
      <th>lifeExp</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Asia</td>
      <td>28.801</td>
      <td>779.445314</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Asia</td>
      <td>30.332</td>
      <td>820.853030</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Asia</td>
      <td>31.997</td>
      <td>853.100710</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Asia</td>
      <td>34.020</td>
      <td>836.197138</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Asia</td>
      <td>36.088</td>
      <td>739.981106</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1699</th>
      <td>Africa</td>
      <td>62.351</td>
      <td>706.157306</td>
    </tr>
    <tr>
      <th>1700</th>
      <td>Africa</td>
      <td>60.377</td>
      <td>693.420786</td>
    </tr>
    <tr>
      <th>1701</th>
      <td>Africa</td>
      <td>46.809</td>
      <td>792.449960</td>
    </tr>
    <tr>
      <th>1702</th>
      <td>Africa</td>
      <td>39.989</td>
      <td>672.038623</td>
    </tr>
    <tr>
      <th>1703</th>
      <td>Africa</td>
      <td>43.487</td>
      <td>469.709298</td>
    </tr>
  </tbody>
</table>
<p>1704 rows × 3 columns</p>
</div>




```python
ad=list(range(1,5,2))
print(df.iloc[:,ad])
```

         continent  lifeExp
    0         Asia   28.801
    1         Asia   30.332
    2         Asia   31.997
    3         Asia   34.020
    4         Asia   36.088
    ...        ...      ...
    1699    Africa   62.351
    1700    Africa   60.377
    1701    Africa   46.809
    1702    Africa   39.989
    1703    Africa   43.487
    
    [1704 rows x 2 columns]
    


```python
print(list(range(3)))
```

    [0, 1, 2]
    


```python
df.loc[[0,1,2],['country','lifeExp']]
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
      <th>country</th>
      <th>lifeExp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>28.801</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Afghanistan</td>
      <td>30.332</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Afghanistan</td>
      <td>31.997</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
