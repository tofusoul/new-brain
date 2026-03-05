- [[Python]] library for manipulating data frames

- [Official User Guide](https://pandas.pydata.org/docs/user_guide/index.html)

- [RTFM](https://pandas.pydata.org/pandas-docs/version/0.23.4/index.html)

- Library Resources

- [1 hour pandas](https://christchurch.bibliocommons.com/v2/record/S37C1236553)

- [pandas data cleaning and modeling](https://learning-oreilly-com.ezproxy.christchurchcitylibraries.com/videos/pandas-data-cleaning/9780135170199/9780135170199-PAND_01_01_03/)

- Series

- Dataframes

- Data Summary

- `df.shape`

- `df.info()`

- `df.describe()`

- Data Conversion

- `pd.to_numeric(series, errors="coerce")`

\*\*

- VS code setup

- add venv, call command pallet and \'python s\' to find command \'python: sellect interpreter\'

- Basic

- example from

[this you tube tutorial](https://www.youtube.com/watch?v=vmEHCJofslg&t=2828s)

- <https://www.youtube.com/watch?v=iYie42M1ZyU&t=1738s>

- the index basically labels the data and allows us to access the data according to the lable

- .loc

- uses index (lables) to access the data

- .iloc

- accesses the data at position specified

- #+BEGIN~SRC~ python

import pandas as pd # imports pandas

poke = pd.read~csv~(\"./pokemon~data~.csv\") # reads the CSV

poke.Name # returns the names

poke\[\'Name\'\] # same as above

poke[[\'Name\', \'HP\']] # returns a table with the columns \'Name\' and \'HP\'

poke.iloc\[1:4\] # returns the rows at index=1 to index=4

poke.iloc\[2,1\]) # returns the data on the 1st column of the 2nd row

for index, row in poke.iterrows(); index, row[[\'Name\', \'HP\']])

poke.loc\[df\[\'Type 1\' = \'Fire\'\]\]

pok.lok\[df\[(\'Type 1\' = \'Fire\') & (\'Attack\' \> 10)\], \[\'Name\', \'Type 1\', \'HP\', \'Attack\'\]\]

poke.describe() # returns the basic stats of the data set like mean, std deviation etc

poke.sort~values~(\'Attack\', ascending=False) \- sorts the pokemons from highest attack to lowest

poke.sort~values~(\[\'Type 1\', \'HP\'\], ascending=\[1,0\]) \- sorts the pokemon by type in alphabetical order, then by attack from highest to lowest

```
#+END_SRC
```
- pasted code to sort

``` python
scrape_status_df.insert(1, 'File Name', np.NaN)
scrape_status_df.insert(7, 'Calculated Quote Value', np.NaN)
```

- Columns and rows

- #+BEGIN~SRC~ python

df.drop()

results~dict~ = dict(\[(k, pd.Series(v)) for k, v in scrape~results~.items()\])

```
#+END_SRC
```
\*

- Example

- Pandas  `dtype`  mapping

  Pandas dtype      Python type    NumPy type                                                        Usage
  ----------------- -------------- ----------------------------------------------------------------- ----------------------------------------------
  object            str or mixed   string\_, unicode\_, mixed types                                  Text or mixed numeric and non-numeric values
  int64             int            int\_, int8, int16, int32, int64, uint8, uint16, uint32, uint64   Integer numbers
  float64           float          float\_, float16, float32, float64                                Floating point numbers
  bool              bool           bool\_                                                            True/False values
  datetime64        NA             datetime64\[ns\]                                                  Date and time values
  timedelta\[ns\]   NA             NA                                                                Differences between two datetimes
  category          NA             NA                                                                Finite list of text values

\*

- To remove all rows where column \'score\' is \< 50:

- df = df.drop(df\[df.score \< 50\].index)

In place version (as pointed out in comments)

- df.drop(df\[df.score \< 50\].index, inplace=True)

Multiple conditions

- (see Boolean Indexing)

- The operators are: \| for or, & for and, and \~ for not. These must be grouped by using parentheses.

- To remove all rows where column \'score\' is \< 50 and \> 20

- df = df.drop(df\[(df.score \< 50) & (df.score \> 20)\].index)

- Data Transformation
```python
df['DOB'] = pd.to~datetime~(df.DOB) df['col'] = 'str' + df['col'].astype(str)
df.toc_sv('filename.csv', index=False) df.to~csv~('example.tsv', sep=")
```
- Looking for information on the data

```pytyhon
df.describe()
df.shape[0]
df.shape[1]
df.dtypes  #list the types of the columns
```

- Multiindex

- [intro guide](https://towardsdatascience.com/how-to-use-multiindex-in-pandas-to-level-up-your-analysis-aeac7f451fce)

- Groupby

- `df.groupby('column').value.agg(func)`

- `df.groupby('col').value.transform(func)`

\*\*

- Functions to look at

- Data frame functions

- aggregate(\[func, axis\])

Aggregate using one or more operations over the specified axis.

- apply(func\[, axis, raw, result~type~, args\])

1.  Apply a function along an axis of the DataFrame.

- drop~duplicates~(\[subset, keep, inplace, ...\])

1.  Return DataFrame with duplicate rows removed.

- equals(other)

1.  Test whether two objects contain the same elements.

- fillna(\[value, method, axis, inplace, ...\])

1.  Fill NA/NaN values using the specified method.

- filter(\[items, like, regex, axis\])

1.  Subset the dataframe rows or columns according to the specified index labels.

- pipes

- <https://towardsdatascience.com/using-pandas-pipe-function-to-improve-code-readability-96d66abfaf8>

- Merge

- <https://www.youtube.com/watch?v=wzN1UyfRSWI>

```python
pd.merge(df1, df2, suffixes=\[\'~L~\', \'~R~\'\], left~on~=\'Count\', right~on~=\'Count\' )
```

- Concat

- conditionally outputs a a column based on two other columns

<https://datagy.io/pandas-conditional-column/>

``` python
#define conditions

conditions = [df['A_points'] > df['B_points'], 
              df['A_points'] < df['B_points']]

#define choices
choices = ['A', 'B']

#create new column in DataFrame that displays results of comparisons
df['winner'] = np.select(conditions, choices, default='Tie')

#view the DataFrame
df

          A_points  B_points  winner
0         1         4         B
1         3         5         B
2         3         2         A
3         3         3         Tie
4         5         2         A
```

\*

- Vectorize a function

- this will let your function run element wise on the dataframe

```python
import numpy as np
@np.vectorize def somefunction(x, y): some~operations~() ...
somefunction(df\[colx\], df\[coly\])
```

- Learning Project
- build a pokedex with the pokemon api
- mostly transform the BNZ CSV into beancount format
- Steps
- Extract just the relevant columns
- Change the date format
- Insert the main account name
- change it into the right order
- put quote marks around payee
- <https://towardsdatascience.com/10-examples-that-will-make-you-use-pandas-query-function-more-often-a8fb3e9361cb>
