Let's first load the dataset


```python
import pandas as pd
```


```python
df = pd.read_csv('exercises_table.csv')
df
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
      <th>Name</th>
      <th>Ex01_Date</th>
      <th>Ex02_Date</th>
      <th>Ex03_Date</th>
      <th>Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Ajay</td>
      <td>12-Jan-2023</td>
      <td>14-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>16-Jan-2023</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Chetan</td>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>19-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Girish</td>
      <td>17-Jan-2023</td>
      <td>NaN</td>
      <td>15-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mohan</td>
      <td>19-Jan-2023</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Vishal</td>
      <td>14-Jan-2023</td>
      <td>15-Jan-2023</td>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
    </tr>
  </tbody>
</table>
</div>



Let's make the "Name" column as the index, so that we can now identify each row by the name of the student


```python
df.set_index('Name', inplace=True)
df
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
      <th>Ex01_Date</th>
      <th>Ex02_Date</th>
      <th>Ex03_Date</th>
      <th>Ex04_Date</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Ajay</th>
      <td>12-Jan-2023</td>
      <td>14-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>16-Jan-2023</td>
    </tr>
    <tr>
      <th>Chetan</th>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>19-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Girish</th>
      <td>17-Jan-2023</td>
      <td>NaN</td>
      <td>15-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Mohan</th>
      <td>19-Jan-2023</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Vishal</th>
      <td>14-Jan-2023</td>
      <td>15-Jan-2023</td>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
    </tr>
  </tbody>
</table>
</div>



One neat trick ( more of a hack though ) to remove the name for the Row index called as "Name" is to set it's name attribute to None


```python
df.index.name = None
df
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
      <th>Ex01_Date</th>
      <th>Ex02_Date</th>
      <th>Ex03_Date</th>
      <th>Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Ajay</th>
      <td>12-Jan-2023</td>
      <td>14-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>16-Jan-2023</td>
    </tr>
    <tr>
      <th>Chetan</th>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>19-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Girish</th>
      <td>17-Jan-2023</td>
      <td>NaN</td>
      <td>15-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Mohan</th>
      <td>19-Jan-2023</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Vishal</th>
      <td>14-Jan-2023</td>
      <td>15-Jan-2023</td>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
    </tr>
  </tbody>
</table>
</div>



How can we find out the students and exercises that were submitted on 18-Jan-2023 and 19-Jan-2023 ?

Let's start by defining the required dates in a list `imp_dates`



```python
imp_dates = ['18-Jan-2023', '19-Jan-2023']
```

Now, we need to check which of the values in `df` contain any of the dates present in `imp_dates`. This can be achieved using `isin` method of DataFrame

This returns a boolean DataFrame with cells that contain any of our values of interest ( any date present in `imp_dates` ) having `True` and the rest as `False`


```python
df.isin(imp_dates)
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
      <th>Ex01_Date</th>
      <th>Ex02_Date</th>
      <th>Ex03_Date</th>
      <th>Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Ajay</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Chetan</th>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Girish</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Mohan</th>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Vishal</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



Let's highlight the cells that contain `True` value using `style` method of DataFrame


```python
(df.isin(imp_dates)
.style
.applymap(lambda x: 'background-color:bisque' 
              if x else '')
)
```




<style type="text/css">
#T_eaaaa_row0_col2, #T_eaaaa_row1_col1, #T_eaaaa_row1_col2, #T_eaaaa_row3_col0, #T_eaaaa_row4_col3 {
  background-color: bisque;
}
</style>
<table id="T_eaaaa_">
  <thead>
    <tr>
      <th class="blank level0" >&nbsp;</th>
      <th class="col_heading level0 col0" >Ex01_Date</th>
      <th class="col_heading level0 col1" >Ex02_Date</th>
      <th class="col_heading level0 col2" >Ex03_Date</th>
      <th class="col_heading level0 col3" >Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="T_eaaaa_level0_row0" class="row_heading level0 row0" >Ajay</th>
      <td id="T_eaaaa_row0_col0" class="data row0 col0" >False</td>
      <td id="T_eaaaa_row0_col1" class="data row0 col1" >False</td>
      <td id="T_eaaaa_row0_col2" class="data row0 col2" >True</td>
      <td id="T_eaaaa_row0_col3" class="data row0 col3" >False</td>
    </tr>
    <tr>
      <th id="T_eaaaa_level0_row1" class="row_heading level0 row1" >Chetan</th>
      <td id="T_eaaaa_row1_col0" class="data row1 col0" >False</td>
      <td id="T_eaaaa_row1_col1" class="data row1 col1" >True</td>
      <td id="T_eaaaa_row1_col2" class="data row1 col2" >True</td>
      <td id="T_eaaaa_row1_col3" class="data row1 col3" >False</td>
    </tr>
    <tr>
      <th id="T_eaaaa_level0_row2" class="row_heading level0 row2" >Girish</th>
      <td id="T_eaaaa_row2_col0" class="data row2 col0" >False</td>
      <td id="T_eaaaa_row2_col1" class="data row2 col1" >False</td>
      <td id="T_eaaaa_row2_col2" class="data row2 col2" >False</td>
      <td id="T_eaaaa_row2_col3" class="data row2 col3" >False</td>
    </tr>
    <tr>
      <th id="T_eaaaa_level0_row3" class="row_heading level0 row3" >Mohan</th>
      <td id="T_eaaaa_row3_col0" class="data row3 col0" >True</td>
      <td id="T_eaaaa_row3_col1" class="data row3 col1" >False</td>
      <td id="T_eaaaa_row3_col2" class="data row3 col2" >False</td>
      <td id="T_eaaaa_row3_col3" class="data row3 col3" >False</td>
    </tr>
    <tr>
      <th id="T_eaaaa_level0_row4" class="row_heading level0 row4" >Vishal</th>
      <td id="T_eaaaa_row4_col0" class="data row4 col0" >False</td>
      <td id="T_eaaaa_row4_col1" class="data row4 col1" >False</td>
      <td id="T_eaaaa_row4_col2" class="data row4 col2" >False</td>
      <td id="T_eaaaa_row4_col3" class="data row4 col3" >True</td>
    </tr>
  </tbody>
</table>




Compare these with the original values of `df` to verify if the results are right

Our values of interest are present in the highligthed cells below


```python

```




<style type="text/css">
#T_75841_row0_col2, #T_75841_row1_col1, #T_75841_row1_col2, #T_75841_row3_col0, #T_75841_row4_col3 {
  background-color: bisque;
}
</style>
<table id="T_75841_">
  <thead>
    <tr>
      <th class="blank level0" >&nbsp;</th>
      <th class="col_heading level0 col0" >Ex01_Date</th>
      <th class="col_heading level0 col1" >Ex02_Date</th>
      <th class="col_heading level0 col2" >Ex03_Date</th>
      <th class="col_heading level0 col3" >Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="T_75841_level0_row0" class="row_heading level0 row0" >Ajay</th>
      <td id="T_75841_row0_col0" class="data row0 col0" >12-Jan-2023</td>
      <td id="T_75841_row0_col1" class="data row0 col1" >14-Jan-2023</td>
      <td id="T_75841_row0_col2" class="data row0 col2" >18-Jan-2023</td>
      <td id="T_75841_row0_col3" class="data row0 col3" >16-Jan-2023</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row1" class="row_heading level0 row1" >Chetan</th>
      <td id="T_75841_row1_col0" class="data row1 col0" >17-Jan-2023</td>
      <td id="T_75841_row1_col1" class="data row1 col1" >18-Jan-2023</td>
      <td id="T_75841_row1_col2" class="data row1 col2" >19-Jan-2023</td>
      <td id="T_75841_row1_col3" class="data row1 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row2" class="row_heading level0 row2" >Girish</th>
      <td id="T_75841_row2_col0" class="data row2 col0" >17-Jan-2023</td>
      <td id="T_75841_row2_col1" class="data row2 col1" >nan</td>
      <td id="T_75841_row2_col2" class="data row2 col2" >15-Jan-2023</td>
      <td id="T_75841_row2_col3" class="data row2 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row3" class="row_heading level0 row3" >Mohan</th>
      <td id="T_75841_row3_col0" class="data row3 col0" >19-Jan-2023</td>
      <td id="T_75841_row3_col1" class="data row3 col1" >nan</td>
      <td id="T_75841_row3_col2" class="data row3 col2" >nan</td>
      <td id="T_75841_row3_col3" class="data row3 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row4" class="row_heading level0 row4" >Vishal</th>
      <td id="T_75841_row4_col0" class="data row4 col0" >14-Jan-2023</td>
      <td id="T_75841_row4_col1" class="data row4 col1" >15-Jan-2023</td>
      <td id="T_75841_row4_col2" class="data row4 col2" >17-Jan-2023</td>
      <td id="T_75841_row4_col3" class="data row4 col3" >18-Jan-2023</td>
    </tr>
  </tbody>
</table>




Now, to filter the rows that contain these dates, we use the values present in the Boolean DataFrame

Let's sum up all the boolean values along each row using `sum(axis=1)`

**Note:** Using `sum()` by default sums the boolean values along each column


```python
df.isin(imp_dates).sum()
```




    Ex01_Date    1
    Ex02_Date    1
    Ex03_Date    2
    Ex04_Date    1
    dtype: int64



Summing the values along each row


```python
df.isin(imp_dates).sum(axis=1)
```




    Ajay      1
    Chetan    2
    Girish    0
    Mohan     1
    Vishal    1
    dtype: int64



We are interested in only those rows that contain atleast one match. So, the sum value for such rows would be > 0

Let's create a mask of the boolean Series for the above comparison 


```python
mask_1819 = df.isin(imp_dates).sum(axis=1) > 0
mask_1819
```




    Ajay       True
    Chetan     True
    Girish    False
    Mohan      True
    Vishal     True
    dtype: bool



Now, let's use the mask to filter the values in the DataFrame


```python
df[mask_1819]
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
      <th>Ex01_Date</th>
      <th>Ex02_Date</th>
      <th>Ex03_Date</th>
      <th>Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Ajay</th>
      <td>12-Jan-2023</td>
      <td>14-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>16-Jan-2023</td>
    </tr>
    <tr>
      <th>Chetan</th>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>19-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Mohan</th>
      <td>19-Jan-2023</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Vishal</th>
      <td>14-Jan-2023</td>
      <td>15-Jan-2023</td>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
    </tr>
  </tbody>
</table>
</div>



Compare the result with the highlighted values from the original DataFrame shown below


```python

```




<style type="text/css">
#T_75841_row0_col2, #T_75841_row1_col1, #T_75841_row1_col2, #T_75841_row3_col0, #T_75841_row4_col3 {
  background-color: bisque;
}
</style>
<table id="T_75841_">
  <thead>
    <tr>
      <th class="blank level0" >&nbsp;</th>
      <th class="col_heading level0 col0" >Ex01_Date</th>
      <th class="col_heading level0 col1" >Ex02_Date</th>
      <th class="col_heading level0 col2" >Ex03_Date</th>
      <th class="col_heading level0 col3" >Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="T_75841_level0_row0" class="row_heading level0 row0" >Ajay</th>
      <td id="T_75841_row0_col0" class="data row0 col0" >12-Jan-2023</td>
      <td id="T_75841_row0_col1" class="data row0 col1" >14-Jan-2023</td>
      <td id="T_75841_row0_col2" class="data row0 col2" >18-Jan-2023</td>
      <td id="T_75841_row0_col3" class="data row0 col3" >16-Jan-2023</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row1" class="row_heading level0 row1" >Chetan</th>
      <td id="T_75841_row1_col0" class="data row1 col0" >17-Jan-2023</td>
      <td id="T_75841_row1_col1" class="data row1 col1" >18-Jan-2023</td>
      <td id="T_75841_row1_col2" class="data row1 col2" >19-Jan-2023</td>
      <td id="T_75841_row1_col3" class="data row1 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row2" class="row_heading level0 row2" >Girish</th>
      <td id="T_75841_row2_col0" class="data row2 col0" >17-Jan-2023</td>
      <td id="T_75841_row2_col1" class="data row2 col1" >nan</td>
      <td id="T_75841_row2_col2" class="data row2 col2" >15-Jan-2023</td>
      <td id="T_75841_row2_col3" class="data row2 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row3" class="row_heading level0 row3" >Mohan</th>
      <td id="T_75841_row3_col0" class="data row3 col0" >19-Jan-2023</td>
      <td id="T_75841_row3_col1" class="data row3 col1" >nan</td>
      <td id="T_75841_row3_col2" class="data row3 col2" >nan</td>
      <td id="T_75841_row3_col3" class="data row3 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_75841_level0_row4" class="row_heading level0 row4" >Vishal</th>
      <td id="T_75841_row4_col0" class="data row4 col0" >14-Jan-2023</td>
      <td id="T_75841_row4_col1" class="data row4 col1" >15-Jan-2023</td>
      <td id="T_75841_row4_col2" class="data row4 col2" >17-Jan-2023</td>
      <td id="T_75841_row4_col3" class="data row4 col3" >18-Jan-2023</td>
    </tr>
  </tbody>
</table>





```python
df.isna().sum(axis=1)
```




    Ajay      0
    Chetan    1
    Girish    2
    Mohan     3
    Vishal    0
    dtype: int64




```python
df.isna().sum(axis=1) > 0
```




    Ajay      False
    Chetan     True
    Girish     True
    Mohan      True
    Vishal    False
    dtype: bool




```python
df_pending = df[df.isna().sum(axis=1) > 0]
df_pending
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
      <th>Ex01_Date</th>
      <th>Ex02_Date</th>
      <th>Ex03_Date</th>
      <th>Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Chetan</th>
      <td>17-Jan-2023</td>
      <td>18-Jan-2023</td>
      <td>19-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Girish</th>
      <td>17-Jan-2023</td>
      <td>NaN</td>
      <td>15-Jan-2023</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Mohan</th>
      <td>19-Jan-2023</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_pending.style.highlight_null('bisque')
```




<style type="text/css">
#T_1d982_row0_col3, #T_1d982_row1_col1, #T_1d982_row1_col3, #T_1d982_row2_col1, #T_1d982_row2_col2, #T_1d982_row2_col3 {
  background-color: bisque;
}
</style>
<table id="T_1d982_">
  <thead>
    <tr>
      <th class="blank level0" >&nbsp;</th>
      <th class="col_heading level0 col0" >Ex01_Date</th>
      <th class="col_heading level0 col1" >Ex02_Date</th>
      <th class="col_heading level0 col2" >Ex03_Date</th>
      <th class="col_heading level0 col3" >Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="T_1d982_level0_row0" class="row_heading level0 row0" >Chetan</th>
      <td id="T_1d982_row0_col0" class="data row0 col0" >17-Jan-2023</td>
      <td id="T_1d982_row0_col1" class="data row0 col1" >18-Jan-2023</td>
      <td id="T_1d982_row0_col2" class="data row0 col2" >19-Jan-2023</td>
      <td id="T_1d982_row0_col3" class="data row0 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_1d982_level0_row1" class="row_heading level0 row1" >Girish</th>
      <td id="T_1d982_row1_col0" class="data row1 col0" >17-Jan-2023</td>
      <td id="T_1d982_row1_col1" class="data row1 col1" >nan</td>
      <td id="T_1d982_row1_col2" class="data row1 col2" >15-Jan-2023</td>
      <td id="T_1d982_row1_col3" class="data row1 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_1d982_level0_row2" class="row_heading level0 row2" >Mohan</th>
      <td id="T_1d982_row2_col0" class="data row2 col0" >19-Jan-2023</td>
      <td id="T_1d982_row2_col1" class="data row2 col1" >nan</td>
      <td id="T_1d982_row2_col2" class="data row2 col2" >nan</td>
      <td id="T_1d982_row2_col3" class="data row2 col3" >nan</td>
    </tr>
  </tbody>
</table>





```python
n_rows, n_cols = df_pending.shape
n_rows
```




    3




```python
df_pending.index
```




    Index(['Chetan', 'Girish', 'Mohan'], dtype='object')




```python
bg_color = [{'selector': 'th', 'props': 'background-color: bisque'}]
label_colors = [bg_color] * n_rows
df_pending.style.set_table_styles(dict(zip(df_pending.index, label_colors)), axis=1)

```




<style type="text/css">
#T_e8e67_ th.row0 {
  background-color: bisque;
}
#T_e8e67_ th.row1 {
  background-color: bisque;
}
#T_e8e67_ th.row2 {
  background-color: bisque;
}
</style>
<table id="T_e8e67_">
  <thead>
    <tr>
      <th class="blank level0" >&nbsp;</th>
      <th class="col_heading level0 col0" >Ex01_Date</th>
      <th class="col_heading level0 col1" >Ex02_Date</th>
      <th class="col_heading level0 col2" >Ex03_Date</th>
      <th class="col_heading level0 col3" >Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="T_e8e67_level0_row0" class="row_heading level0 row0" >Chetan</th>
      <td id="T_e8e67_row0_col0" class="data row0 col0" >17-Jan-2023</td>
      <td id="T_e8e67_row0_col1" class="data row0 col1" >18-Jan-2023</td>
      <td id="T_e8e67_row0_col2" class="data row0 col2" >19-Jan-2023</td>
      <td id="T_e8e67_row0_col3" class="data row0 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_e8e67_level0_row1" class="row_heading level0 row1" >Girish</th>
      <td id="T_e8e67_row1_col0" class="data row1 col0" >17-Jan-2023</td>
      <td id="T_e8e67_row1_col1" class="data row1 col1" >nan</td>
      <td id="T_e8e67_row1_col2" class="data row1 col2" >15-Jan-2023</td>
      <td id="T_e8e67_row1_col3" class="data row1 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_e8e67_level0_row2" class="row_heading level0 row2" >Mohan</th>
      <td id="T_e8e67_row2_col0" class="data row2 col0" >19-Jan-2023</td>
      <td id="T_e8e67_row2_col1" class="data row2 col1" >nan</td>
      <td id="T_e8e67_row2_col2" class="data row2 col2" >nan</td>
      <td id="T_e8e67_row2_col3" class="data row2 col3" >nan</td>
    </tr>
  </tbody>
</table>





```python
df.style.set_table_styles(dict(zip(df_pending.index, label_colors)), axis=1)

```




<style type="text/css">
#T_99bcf_ th.row1 {
  background-color: bisque;
}
#T_99bcf_ th.row2 {
  background-color: bisque;
}
#T_99bcf_ th.row3 {
  background-color: bisque;
}
</style>
<table id="T_99bcf_">
  <thead>
    <tr>
      <th class="blank level0" >&nbsp;</th>
      <th class="col_heading level0 col0" >Ex01_Date</th>
      <th class="col_heading level0 col1" >Ex02_Date</th>
      <th class="col_heading level0 col2" >Ex03_Date</th>
      <th class="col_heading level0 col3" >Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="T_99bcf_level0_row0" class="row_heading level0 row0" >Ajay</th>
      <td id="T_99bcf_row0_col0" class="data row0 col0" >12-Jan-2023</td>
      <td id="T_99bcf_row0_col1" class="data row0 col1" >14-Jan-2023</td>
      <td id="T_99bcf_row0_col2" class="data row0 col2" >18-Jan-2023</td>
      <td id="T_99bcf_row0_col3" class="data row0 col3" >16-Jan-2023</td>
    </tr>
    <tr>
      <th id="T_99bcf_level0_row1" class="row_heading level0 row1" >Chetan</th>
      <td id="T_99bcf_row1_col0" class="data row1 col0" >17-Jan-2023</td>
      <td id="T_99bcf_row1_col1" class="data row1 col1" >18-Jan-2023</td>
      <td id="T_99bcf_row1_col2" class="data row1 col2" >19-Jan-2023</td>
      <td id="T_99bcf_row1_col3" class="data row1 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_99bcf_level0_row2" class="row_heading level0 row2" >Girish</th>
      <td id="T_99bcf_row2_col0" class="data row2 col0" >17-Jan-2023</td>
      <td id="T_99bcf_row2_col1" class="data row2 col1" >nan</td>
      <td id="T_99bcf_row2_col2" class="data row2 col2" >15-Jan-2023</td>
      <td id="T_99bcf_row2_col3" class="data row2 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_99bcf_level0_row3" class="row_heading level0 row3" >Mohan</th>
      <td id="T_99bcf_row3_col0" class="data row3 col0" >19-Jan-2023</td>
      <td id="T_99bcf_row3_col1" class="data row3 col1" >nan</td>
      <td id="T_99bcf_row3_col2" class="data row3 col2" >nan</td>
      <td id="T_99bcf_row3_col3" class="data row3 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_99bcf_level0_row4" class="row_heading level0 row4" >Vishal</th>
      <td id="T_99bcf_row4_col0" class="data row4 col0" >14-Jan-2023</td>
      <td id="T_99bcf_row4_col1" class="data row4 col1" >15-Jan-2023</td>
      <td id="T_99bcf_row4_col2" class="data row4 col2" >17-Jan-2023</td>
      <td id="T_99bcf_row4_col3" class="data row4 col3" >18-Jan-2023</td>
    </tr>
  </tbody>
</table>




- dummy


```python
(df
.style
.applymap(lambda x: 'background-color:bisque' 
              if x in imp_dates else None)
)
```




<style type="text/css">
#T_46235_row0_col2, #T_46235_row1_col1, #T_46235_row1_col2, #T_46235_row3_col0, #T_46235_row4_col3 {
  background-color: bisque;
}
</style>
<table id="T_46235_">
  <thead>
    <tr>
      <th class="blank level0" >&nbsp;</th>
      <th class="col_heading level0 col0" >Ex01_Date</th>
      <th class="col_heading level0 col1" >Ex02_Date</th>
      <th class="col_heading level0 col2" >Ex03_Date</th>
      <th class="col_heading level0 col3" >Ex04_Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="T_46235_level0_row0" class="row_heading level0 row0" >Ajay</th>
      <td id="T_46235_row0_col0" class="data row0 col0" >12-Jan-2023</td>
      <td id="T_46235_row0_col1" class="data row0 col1" >14-Jan-2023</td>
      <td id="T_46235_row0_col2" class="data row0 col2" >18-Jan-2023</td>
      <td id="T_46235_row0_col3" class="data row0 col3" >16-Jan-2023</td>
    </tr>
    <tr>
      <th id="T_46235_level0_row1" class="row_heading level0 row1" >Chetan</th>
      <td id="T_46235_row1_col0" class="data row1 col0" >17-Jan-2023</td>
      <td id="T_46235_row1_col1" class="data row1 col1" >18-Jan-2023</td>
      <td id="T_46235_row1_col2" class="data row1 col2" >19-Jan-2023</td>
      <td id="T_46235_row1_col3" class="data row1 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_46235_level0_row2" class="row_heading level0 row2" >Girish</th>
      <td id="T_46235_row2_col0" class="data row2 col0" >17-Jan-2023</td>
      <td id="T_46235_row2_col1" class="data row2 col1" >nan</td>
      <td id="T_46235_row2_col2" class="data row2 col2" >15-Jan-2023</td>
      <td id="T_46235_row2_col3" class="data row2 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_46235_level0_row3" class="row_heading level0 row3" >Mohan</th>
      <td id="T_46235_row3_col0" class="data row3 col0" >19-Jan-2023</td>
      <td id="T_46235_row3_col1" class="data row3 col1" >nan</td>
      <td id="T_46235_row3_col2" class="data row3 col2" >nan</td>
      <td id="T_46235_row3_col3" class="data row3 col3" >nan</td>
    </tr>
    <tr>
      <th id="T_46235_level0_row4" class="row_heading level0 row4" >Vishal</th>
      <td id="T_46235_row4_col0" class="data row4 col0" >14-Jan-2023</td>
      <td id="T_46235_row4_col1" class="data row4 col1" >15-Jan-2023</td>
      <td id="T_46235_row4_col2" class="data row4 col2" >17-Jan-2023</td>
      <td id="T_46235_row4_col3" class="data row4 col3" >18-Jan-2023</td>
    </tr>
  </tbody>
</table>



