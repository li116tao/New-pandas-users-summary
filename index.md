# New-pandas-users-summary
This is a summary of basic functions and concepts from pandas tutorial for new users, focusing on creating dataFrame, grouping, IO, lambda, selecting data and handling indexs etc the very necessity of using pandas. 

I first list the functions together to give a overview :
## List of functions:
[references--from pandas documentation](https://pandas.pydata.org/pandas-docs/version/0.15/tutorials.html)
### **Remeber coding is a LANGUAGE, to be able to speak that language, you need to remember the words first. The functions below are the words, finding oppotunities to use them over and over again. Even if you may not know exactly, you will develop a sense along the way.** 

- list
- zip
> **list(zip(names, numbers))**
- pd.DataFrame(data = , columns=[])
- df.to_csv
- pd.read_csv
- df.types (check datatype of column)
- df.sort_values([column_name], ascending = True or False )
- df.sort_index(axis=0)

- random.seed()
- random.randint(low = , high = )

> **random_names = [names[random.randint(low=0 high = len(names))] for i in range(1000)]**

- len
- range
- df.info()
- df.describe()
- df[column_name].unique()

- df.groupby('index')
- df.groupby().sum()

- def function():
   return

- pd.read_excel(path, index_col = )
- df.index

> **df['State'] = df.State.apply(lambda x: x.upper())**
> **df = df[df['Status'] == 1] boolean indexing**

- df.reset_index()
> **Daily = df.reset_index().groupby(['State','StatusDate']).sum()**

- del df[column_name]
- df.index.levels[0]

> **StateYearMonth = Daily.groupby([Daily.index.get_level_values(0), Daily.index.get_level_values(1).year, Daily.index.get_level_values(1).month])**
> **Daily['Lower'] = StateYearMonth['CustomerCount'].transform(lambda x: x.quantile(q=.25) - (1.5x.quantile(q=.75) - x.quantile(q=.25)))**
> **YearMonth = All.groupby([lambda x: x.year, lambda x:x.month])**

- idx = pd.date_range(start = , end = , freq= )
- df = pd.DataFrame(data, index = idx, columns = [columns_name])
- pd.concat()
> **Year = combined.gropupby(lambda x:x.year).max()**
- df.pct_change(periods = )

- df.iloc[0:3]
- df[column_name]
- df.loc[df.index[0:3], column_name]

> **d = {'one':[1,1], 'two':[2,2]}**
> **i = ['a', 'b']**
> **df = pd.DataFrame(data = d, index = i)**


```
     one	two
  a	1	2
  b	1	2
```

- df.stack()

```

 a  one    1
    two    2
 b  one    1
    two    2
```

- df.unstack()

```

 one  a    1
      b    1
 two  a    2
      b    2
```

- df.T

```
        a  b
 one	  1	1
 two	  2	2
```

- df.copy()

> calculate outlier
> **newdf['Outlier'] = State.transform(lambda x: abs(x-x.mean()) > 1.96x.std())**
- df.to_json()
- df.pd.read_json()
> combining data from different resource

> 1.getting file name list


```
FileNames = []
os.chdir(r"path")
for files in os.listdir('.'):
    if files.endswith(".xlsx"):
        FileName.append(files)
```

>2. getting files

```

def GetFile(fnambre):
    location = r'path\' + fnambre
    df = pd.read_excel(location, 0)
    df['File'] = fnambre
    return df.set_index([File])
```

>3.Creating a list of dataframes

```

df_list = [GetFile(fname) for fname in FileNames]
big_df = pd.concat(df_list)
```
## showcase example of using the above functions
####
I first created a large dataset using random generator from numpy. It randomly pick an element from the lists, used for loop to repeat this process to generate a large data size, it can be as large as you wish!
Used function date-range to generate date as index later. Set data, column and row index to form a dataset used to be analized later to practice more functions.

The second part of the example is to analyse this dataset. In general, before any specific analysis, we need to have an idea about the entire datase. what are the rows, columns, is there any missing data, is the dataset correct or not etc. After that we need to use some functions to manipulate data in order to get and present information. The most often used functions are groupby, sort_index, sort_values to form a sub dataset, some calculations, and some more fancy technics e.g chained functions, df.transfrom and lambda. 

For example:to answer the question "Does the popularity of names change with time?"
we first sort index with time descending order, add one column to calculate the number of names, then reset index group dataset by names, the info we are looking for can be easily seen. Chained function is used.

# Pandas cookbook summary
This is a supplyment of the first section. From pandas cookbook. 
[References--Pandas documentaion pandas cookbook](https://nbviewer.jupyter.org/github/jvns/pandas-cookbook/blob/v0.1/cookbook/Chapter%201%20-%20Reading%20from%20a%20CSV.ipynb)
## List of functions:
- pd.read_csv('path', sep = ':', encoding='Latins1', parse_dates=['Date'], dayfirst=True, index_col = 'Date')
- df[column_name].plot(kind = )
### Dealing with columns that is text represnts different item ###
- df[column_name].value_counts()
### a more serious slicing and dicing ###
- df[colum_name1 == 'condition' & column_name2 == 'condition']

- astype(float)
- df.index.weekday
- 



