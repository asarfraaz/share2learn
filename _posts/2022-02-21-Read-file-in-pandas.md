---
title : Different ways of reading csv file using Pandas
date : 2022-02-22
author : Basavaraj
category : Tutorial
---

# Pandas
Lets try to understand what exactly pandas is.
Pandas is a one of the python library, and it is used to analyze data.
And it is widly used in the datascience and data analytics.

- So today we will discuss about the how read the file in the pandas,
- and which are the ways to read the data from the pandas.
- There are many wasy to read many kind of data in pandas like.
- read_csv, 
- read_json, 
- read_html, 
- read_excel, 
- read_fwf, 
- read_gbq, 
- read_orc,
- read_pickle,etc
- before that we need to import the pandas package.
# import pandas as pd
# So in this blog we will discuss how to read data from the csv read_csv().
- There are more then 13 ways to read the file from the pandas read function.
## Ex 1: Read csv file normally so it read with header row.
- we use read_csv() function to read the data in the csv file.
  - mydata = read_csv('your_file_name.csv')
  - So here we are reading the file from the csv with header
  - if we dont want the header we can use the header parameter header=False,

## Ex 2: Read csv file with header in second row.
- if we want to make second row of the csv is the header row of the date
- we can set this header parameter with the indexing.
- mydata = pd.read_csv("your_file_name.csv", header = 1)
- So now pandas make the second line will be the header of the data

## Ex 3: Read csv file with your own columns insted of default ones.
- mydata = pd.read_csv("your_file_name.csv", skiprows=1, names=['CustID', 'Name', 'Companies', 'Income'])

- Here we are ignoring the first row that is header row insted of default headers
- we are passing new header names to the data.
- here skiprows = 1 it will skip the first row of the file.
- here names = [....] it will the pass the new column names to the csv.

## Ex 4: Skip rows but keep header
- mydata = pd.read_csv("your_file_name.csv", skiprows=[1,2])

- So here we are always remember indexes always start from 0.
- here we are skipping the second and third rows while importing the data it means while reading.

## Ex 5:Read csv file without header row
- for this we need to use "header = None" 
- mydata = pd.read_csv("your_file_name.csv", header = None)
- It means there is no header insted of header the pandas will create a header names like 0,1,2,3 so on

- mydata = pd.read_csv("your_file_name.csv", header = None, prefix="var") 
- So prefix= "var" here we are creating column name insted of 0,1,2,3,... we are passing one default string called "var"

## Ex 6: Specify missing values
- here we are specifing the missing values with the special paramere.
- If our data is containing any blank spaces like " ", "" so this kind of data 
- To identify this kind of data is a null data means nothing is there in that.
- mydata = pd.read_csv("your_file_name.csv", na_values=['.'])
- so na_values = (['.']) it means we are the blank spaces are there in the data
- there we are creating value called "NaN" emptpy.

## Ex 7: Set index column
- here we are creating the index with particular column name.
- mydata = pd.read_csv("your_file_name.csv", index_col ='ID')

## Ex 8: Reading file from the External URL
- Pandas allows us to read the file from the web
- ex if we want to load the data from the kaggle are github we cant just menstion the url is enogh.
- mydata = pd.read_csv("http://winterolympicsmedals.com/medals.csv")
- so we are using github url to load the csv file.

## Ex 9: Skipping last 5 rows while importing the csv.
- mydata = pd.read_csv("http://winterolympicsmedals.com/medals.csv", skip_footer=5)
- It will skipp the last five rows while importing the csv using skip_footer method.

## Ex 10: Read only specific columns
- here if we want to read some specific columns for the file we use
- mydata = pd.read_csv("http://winterolympicsmedals.com/medals.csv", usecols=[1,5,7])

## Ex 11: Read some perticular rows and columns
- mydata = pd.read_csv("http://winterolympicsmedals.com/medals.csv", usecols=[1,5,7], nrows=5)
- here usecols and nrows are specifing the how much data need to read.

## Ex 12: Read file with the semi colon delimiter
- here some of the data is not seperated by comma (',') for tose type of data we use to read based on thier delimiter.
- mydata = pd.read_csv("file_path_with_file_name", sep = ';')

## Ex 13: Change column type while importing csv.
- mydf = pd.read_csv("workingfile.csv", dtype = {"salary" : "float64"})
- Suppose if you want to change the data data type of the column while importing column.
- we use parameter called dtype = 'int' or 'float'

- So finally these are the things to read the csv file from the pandas read_csv_functions.
- 
