---
title: "Add a row in Pandas"
date: 2023-07-14
author: Sarfraaz Ahmed
category: Tutorial
---

<p align="center">
<a data-flickr-embed="true" data-header="true" data-footer="true" href="https://www.flickr.com/photos/s_raaz/313020754/" title="Bangalore Winter"><img src="https://live.staticflickr.com/119/313020754_e369b25de7_w.jpg" width="400" height="300" alt="Bangalore Winter"/></a>
<br>
Photo by <a href="https://www.flickr.com/photos/s_raaz/313020754/">Sarfraaz Ahmed</a>, all rights reserved
</p>

Things to learn in this post
- Adding a single row to the end of an existing DataFrame
- Adding a single row to the top of an existing DataFrame
- Adding a single row at any given position of an existing DataFrame

Often, while working with Pandas in the backend of a system, we might collect single input data from the frontend, be it a web interface or GUI interface. We might want to add this new data to an existing DataFrame. 

Or may be we get the new usage data from the user's interaction with our deployed machine learning model and we need to collect this input and add it back to our learning dataset. This updated learning dataset can be used to improve the machine learning algorithm built using it.

In all such scenarios, we would want to add a new row to an existing DataFrame. It's pretty straight forward to add a new column to an existing DataFrame and this is more often done in Data Analytics. 

But adding a new row is not so straight forward. Let's learn to add a row to a DataFrame with an example.

## Creating a DataFrame

Assume we have a DataFrame of Indian cricket players as shown below

```python
    [1] df = pd.DataFrame({ 'Name'  : ['Sachin', 'Ganguly', 'Dravid', 'Laxman'],
                            'Runs'  : [99, 120, 56, 70],
                            'Balls' : [120, 80, 115, 85]
                  })

    [2] df
```

Output : DataFrame with 4 rows

<div>
<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sachin</td>
      <td>99</td>
      <td>120</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ganguly</td>
      <td>120</td>
      <td>80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dravid</td>
      <td>56</td>
      <td>115</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Laxman</td>
      <td>70</td>
      <td>80</td>
    </tr>
  </tbody>
</table>
</div>

Digressing from the topic here, but let's try another easy way to create the same DataFrame, by writing the data in the form of rows ( which I think is more easy for humans to interpret ) This can be done using ```from_records``` method

```python
    [1] names = "Sachin Ganguly Dravid Laxman".split()
    [2] runs = [99, 120, 56, 70]
    [3] balls = [120, 80, 150, 85]

    [4] rows = zip(names, runs, balls) # list of triplets
    [5] print(list(rows))
```

Output : List of row elements

```bash
[('Sachin', 99, 120),
 ('Ganguly', 120, 80),
 ('Dravid', 56, 150),
 ('Laxman', 70, 85)]
```

Let's now add column names to each field in these rows and create a DataFrame :

```python
    [1] col_names = "Name Runs Balls".split()
    [2] df = pd.DataFrame.from_records(rows, columns = col_names)
    [3] df 
```

Output : DataFrame with 4 rows

<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sachin</td>
      <td>99</td>
      <td>120</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ganguly</td>
      <td>120</td>
      <td>80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dravid</td>
      <td>56</td>
      <td>115</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Laxman</td>
      <td>70</td>
      <td>80</td>
    </tr>
  </tbody>
</table>


We now want to add information about another player, Dhoni to this DataFrame. The data is as follows :

```python
    [1] new_name = "Dhoni"
    [2] new_runs = 38
    [3] new_balls = 30
```

To add this to the existing DataFrame, we first need to create a separate DataFrame containing only this new information. We can then concatenate both the DataFrames

To create a separate DataFrame for Dhoni's information, we need to create a list of rows as earlier, except that this list would contain only one row with information about Dhoni only

```python
    [1] row_data = (new_name, new_runs, new_balls)
    [2] rows = [row_data] # list of triplets
    [3] print(rows)
```

Output: A list of single row elements

```bash
    [('Dhoni', 38, 30)]
```

We can now pass this list of rows to ```from_records``` method to create a DataFrame

```python
    [1] new_df = ( pd
    [2]           .DataFrame
    [3]           .from_records(rows,
    [4]                         columns=df.columns
    [5]                         )
    [6]          )

    [7] new_df             
```

Output : The single row DataFrame


<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Dhoni</td>
      <td>38</td>
      <td>30</td>
    </tr>
  </tbody>
</table>

We specify ```columns=df.columns``` to make sure that the separate DataFrame also uses the same column names as the earlier one

## Append new row to the end of existing DataFrame

To append the new row to the end of the existing DataFrame, we use ```concat``` method 

```concat``` method expects a list of DataFrames. Make sure you specify the existing DataFrame before the single row DataFrame in this list. This will make sure that the single row DataFrame gets added to the end of the existing DataFrame

```python
    [1] # The order of DataFrames determines position of new row
    [2] dfs = [df, new_df]
    [3] pd.concat(dfs).reset_index(drop=True)
```

Output : New row (Dhoni) gets added at the end of existing DataFrame


<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sachin</td>
      <td>99</td>
      <td>120</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ganguly</td>
      <td>120</td>
      <td>80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dravid</td>
      <td>56</td>
      <td>115</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Laxman</td>
      <td>70</td>
      <td>80</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dhoni</td>
      <td>38</td>
      <td>30</td>
    </tr>
  </tbody>
</table>


Dhoni is added with row label 4

## Add new row to the top of existing DataFrame

We use ```concat``` method as earlier to add the new row to the top of the existing DataFrame. But, we change the order of the DataFrames mentioned in the list passed to ```concat``` method. We first specify the single row DataFrame and then specify the existing DataFrame.


```python
    [1] # The order of DataFrames determines position of new row
    [2] dfs = [new_df, df]
    [3] pd.concat(dfs).reset_index(drop=True)
```

Output : New row (Dhoni) gets added at the top of existing DataFrame


<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Dhoni</td>
      <td>38</td>
      <td>30</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sachin</td>
      <td>99</td>
      <td>120</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ganguly</td>
      <td>120</td>
      <td>80</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Dravid</td>
      <td>56</td>
      <td>115</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Laxman</td>
      <td>70</td>
      <td>80</td>
    </tr>
  </tbody>
</table>


Dhoni is added with row label 0


## Insert new row at any position of existing DataFrame

Let's say we want to add the new row (Dhoni) after 2 rows. To solve this, we need to split existing DataFrame into 2 pieces.

The first piece would contain the first 2 rows

```python
    [1] rowidx = 2
    [2] df.iloc[:rowidx]
```

Output : First 2 rows of existing DataFrame

<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sachin</td>
      <td>99</td>
      <td>120</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ganguly</td>
      <td>120</td>
      <td>80</td>
    </tr>
  </tbody>
</table>


The second piece would contain all rows except the first 2 rows

```python
    [1] rowidx = 2
    [2] df.iloc[rowidx:]
```

Output : All rows except the first 2 rows of existing DataFrame

<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Dravid</td>
      <td>56</td>
      <td>115</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Laxman</td>
      <td>70</td>
      <td>80</td>
    </tr>
  </tbody>
</table>


We can now concatenate these 2 pieces while keeping the single row DataFrame in between them :

```python
    [1] # Insert after 2 rows
    [2] rowidx = 2 # insert as row index 2
    [3] ( pd.concat(
    [4]            [ df.iloc[:rowidx], # first two rows
    [5]              new_df,           # the new row
    [6]              df.iloc[rowidx:]  # from third row onwards
    [7]            ]
    [8]           )
    [9]      .reset_index(drop=True)
    [10] )
```

Output : New row inserted after after first 2 rows of existing DataFrame

<table border="1" style="table-layout: auto;">
  <thead style="text-align: right;">
    <tr style="text-align: center;">
      <th></th>
      <th>Name</th>
      <th>Runs</th>
      <th>Balls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sachin</td>
      <td>99</td>
      <td>120</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ganguly</td>
      <td>120</td>
      <td>80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Dhoni</td>
      <td>38</td>
      <td>30</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Dravid</td>
      <td>56</td>
      <td>115</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Laxman</td>
      <td>70</td>
      <td>80</td>
    </tr>
  </tbody>
</table>

Dhoni is added with row label 2

## Learnings

In this blog post we have learnt to
- Create a DataFrame using a dictionary
- Create a DataFrame using a list of rows
- Adding a new row to the end of an existing DataFrame
- Adding a new row to the top of an existing DataFrame
- Adding a new row at any position of an existing DataFrame

