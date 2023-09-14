---
layout: post
title:  "Blazing through numpy basics - 2"
date:   2023-04-13 21:48:43 +0530
categories: ml, ai, notes
---
## Pandas basics[¶](#Pandas-basics)

- pandas is a Python library that allows us to perform data analysis.
    
- pandas can deal with one and 2 dimensional data.
    
- For one-dimensional data, we use pandas.Series and for two dimensional data we use DataFrame.
    
- Each element in the Series has an index. By default the index is an integer starting with 0.
    
- We can add custom indexes using the "index" keyword.
    

In [ ]:

```
import pandas as pd
import numpy as np

# Create a series with 4 random numbers
s = pd.Series(np.random.randn(4))
print(s)

# Create a series with 4 random numbers and an index
s = pd.Series(np.random.randn(4), index=['a', 'b', 'c', 'd'])
print(s)

# Create a series from a dictionary
d = {'b' : 1, 'a' : 0, 'c' : 2}
s = pd.Series(d)
print(s)

# Create a series from a dictionary with an index
# notice the NaN values for the missing keys
d = {'b' : 1, 'a' : 0, 'c' : 2}
s = pd.Series(d, index=['b', 'c', 'd', 'a'])
print(s)
```

```
0   -0.445945
1   -1.320692
2    1.461804
3   -0.436413
dtype: float64
a    0.875488
b    0.213897
c   -0.542498
d   -1.224826
dtype: float64
b    1
a    0
c    2
dtype: int64
b    1.0
c    2.0
d    NaN
a    0.0
dtype: float64
```

## DataFrame[¶](#DataFrame)

- DataFrames help us work with tabular data.
    
- The labels for rows is specified by "index" keyword, for columns it is specified by "columns" keyword.
    

In [ ]:

```
# DataFrame with random numbers and column labels
df = pd.DataFrame(np.random.randn(10, 4), columns=['A', 'B', 'C', 'D'])
print(df)
```

```
          A         B         C         D
0 -1.193820 -0.983276  1.427023  1.749793
1  0.589161  0.287724 -1.014136  0.430994
2  0.182868 -0.948361 -0.435162  0.717837
3  0.952992  0.728620  2.073391 -0.585289
4 -0.741834  0.512742  0.913819  0.855094
5 -0.287674  0.739805 -0.952221 -0.283430
6  0.319395  1.186191  0.439914 -0.910460
7 -0.441900 -0.045551  0.486682 -0.797498
8 -0.726187 -1.472991 -1.313478  0.784341
9  1.150074 -0.815494  0.387999 -0.751721
```

In [ ]:

```
# DataFrame with random numbers and both row and column labels
df = pd.DataFrame(np.arange(10).reshape(5, 2),index=['a','b','c','d','e'], columns=['A', 'B'])
print(df)

# DataFrame from a scalar dictionary. 
# Here you cannot create a DataFrame from a scalar dictionary without passing an index
df = pd.DataFrame({'a':1,'b':3,'c':4}, index=[0,1,2])
print(df)
```

```
   A  B
a  0  1
b  2  3
c  4  5
d  6  7
e  8  9
   a  b  c
0  1  3  4
1  1  3  4
2  1  3  4
```

## Upcasting[¶](#Upcasting)

- In DataFrames, if the data is of mixed type, the upcasting occurs at the per-column basis.
    
- This is similar to how you would format values in a spreadsheet.
    

In [ ]:

```
# DataFrame upcasting
# Notice each column is upcasted to the most suitable type
df = pd.DataFrame({'A' : [1.,2.],'B':[2,3], 'C':['hello',1]}, index=[0,1])
print(df, '\n')
print(df.dtypes)
```

```
     A  B      C
0  1.0  2  hello
1  2.0  3      1 

A    float64
B      int64
C     object
dtype: object
```

## Appending data to DataFrames[¶](#Appending-data-to-DataFrames)

- We can append data to the DataFrame, either using a Series or another DataFrame.
    
- append function now is being deprecated in favour of concat.
    

In [ ]:

```
# concat data frames
df1 = pd.DataFrame(np.random.randn(4, 4))
print(df1, '\n')
df2 = pd.DataFrame(np.random.randn(3, 3))
print(df2, '\n')

# axis=0 means concat along the rows
df3 = pd.concat([df1, df2], axis=0)
print(df3, '\n')

# axis=1 means concat along the columns
df4 = pd.concat([df1, df2], axis=1)
print(df4, '\n')
```

```
          0         1         2         3
0 -0.460343 -0.253981 -0.656827 -0.465146
1 -0.951850  0.357795 -0.679560  0.394420
2 -1.165198  0.913833  1.721618 -0.660461
3 -1.692367 -0.842518 -1.051814  0.745066 

          0         1         2
0  0.690215  0.039695  0.085907
1 -1.268703  1.787401 -1.172152
2  0.427027  0.892476 -0.782744 

          0         1         2         3
0 -0.460343 -0.253981 -0.656827 -0.465146
1 -0.951850  0.357795 -0.679560  0.394420
2 -1.165198  0.913833  1.721618 -0.660461
3 -1.692367 -0.842518 -1.051814  0.745066
0  0.690215  0.039695  0.085907       NaN
1 -1.268703  1.787401 -1.172152       NaN
2  0.427027  0.892476 -0.782744       NaN 

          0         1         2         3         0         1         2
0 -0.460343 -0.253981 -0.656827 -0.465146  0.690215  0.039695  0.085907
1 -0.951850  0.357795 -0.679560  0.394420 -1.268703  1.787401 -1.172152
2 -1.165198  0.913833  1.721618 -0.660461  0.427027  0.892476 -0.782744
3 -1.692367 -0.842518 -1.051814  0.745066       NaN       NaN       NaN 

```

## Dropping data from DataFrame[¶](#Dropping-data-from-DataFrame)

- We use the "drop" function to remove rows or columns from a given DataFrame.
    
- Notice how the drop function returns a new DataFrame while keeping the original unmodified.
    

In [ ]:

```
# drop data from a DataFrame
df = pd.DataFrame(np.random.randn(4, 4))
print(df, '\n')

# drop the first row
df1 = df.drop(df.index[0])
print(df1, '\n')

# drop the first and last row
df2 = df.drop(df.index[[0,-1]])
print(df2, '\n')

# drop the first column
df3 = df.drop(df.columns[0], axis=1)
print(df3, '\n')

# drop both the first row and last column
# notice the use of the drop method twice
df4 = df.drop(df.index[0]).drop(df.columns[-1], axis=1)
print(df4, '\n')
```

```
          0         1         2         3
0 -0.140739 -0.574950  1.123004  0.061094
1 -1.325015 -0.047437 -0.662744  1.090997
2 -0.282725 -0.115141 -0.676267  0.788252
3 -0.154298  0.964851  0.274268 -1.074325 

          0         1         2         3
1 -1.325015 -0.047437 -0.662744  1.090997
2 -0.282725 -0.115141 -0.676267  0.788252
3 -0.154298  0.964851  0.274268 -1.074325 

          0         1         2         3
1 -1.325015 -0.047437 -0.662744  1.090997
2 -0.282725 -0.115141 -0.676267  0.788252 

          1         2         3
0 -0.574950  1.123004  0.061094
1 -0.047437 -0.662744  1.090997
2 -0.115141 -0.676267  0.788252
3  0.964851  0.274268 -1.074325 

          0         1         2
1 -1.325015 -0.047437 -0.662744
2 -0.282725 -0.115141 -0.676267
3 -0.154298  0.964851  0.274268 

```

## Accessing elements from a DataFrame[¶](#Accessing-elements-from-a-DataFrame)

In [ ]:

```
# accessing elements from a DataFrame
df = pd.DataFrame(np.random.randn(4, 4), columns=['A', 'B', 'C', 'D'])
print(df, '\n')

# access the first row
print(df.iloc[0], '\n')

# access the first column
print(df.iloc[:,0], '\n')

# access the first row and first column
print(df.iloc[0,0], '\n')

# access the first row and first two columns
print(df.iloc[0,0:2], '\n')

# access first and third row
print(df.iloc[[0,2]], '\n')
```

```
          A         B         C         D
0 -0.662594 -0.441515  0.866200 -1.470496
1 -0.431025 -1.138972 -0.779091 -0.361117
2  2.166971  0.217546 -0.613830 -1.316171
3 -0.733857  0.665479 -1.052862 -0.414867 

A   -0.662594
B   -0.441515
C    0.866200
D   -1.470496
Name: 0, dtype: float64 

0   -0.662594
1   -0.431025
2    2.166971
3   -0.733857
Name: A, dtype: float64 

-0.6625944367464723 

A   -0.662594
B   -0.441515
Name: 0, dtype: float64 

          A         B        C         D
0 -0.662594 -0.441515  0.86620 -1.470496
2  2.166971  0.217546 -0.61383 -1.316171 

```

## Grouping data[¶](#Grouping-data)

In [ ]:

```
# groupby demo with a DataFrame
df = pd.DataFrame({'A' : ['foo', 'bar', 'foo', 'bar',
                            'foo', 'bar', 'foo', 'foo'],
                    'B' : ['one', 'one', 'two', 'three',
                            'two', 'two', 'one', 'three'],
                    'C' : np.random.randn(8),
                    'D' : np.random.randn(8)})
print(df, '\n')

# group by A and sum the values in C
print(df.groupby('A').sum(), '\n')

# group by A and B and sum the values in C
print(df.groupby(['A','B']).sum(), '\n')
```

```
     A      B         C         D
0  foo    one -0.191712  0.290158
1  bar    one -1.148870  0.269147
2  foo    two  1.446640 -0.494523
3  bar  three  0.215122  1.522865
4  foo    two  0.030655 -1.038506
5  bar    two -1.103106  0.768592
6  foo    one -0.285698  0.500283
7  foo  three  0.492722  0.518543 

            C         D
A                      
bar -2.036854  2.560605
foo  1.492607 -0.224044 

                  C         D
A   B                        
bar one   -1.148870  0.269147
    three  0.215122  1.522865
    two   -1.103106  0.768592
foo one   -0.477410  0.790441
    three  0.492722  0.518543
    two    1.477295 -1.533029 

```

In [ ]:

```
# sorting demo with a DataFrame
df = pd.DataFrame({'A' : ['foo', 'bar', 'foo', 'bar',
                            'foo', 'bar', 'foo', 'foo'],
                    'B' : ['one', 'one', 'two', 'three',
                            'two', 'two', 'one', 'three'],
                    'C' : np.random.randn(8),
                    'D' : np.random.randn(8)})
print(df, '\n')

# sort by column A
print(df.sort_values(by='A'), '\n')

# sort by column A and then by column B
print(df.sort_values(by=['A','B']), '\n')

# sort by column A in descending order
print(df.sort_values(by='A', ascending=False), '\n')

# sort by column A and then by column B in descending order
print(df.sort_values(by=['A','B'], ascending=[True,False]), '\n')
```

```
     A      B         C         D
0  foo    one -1.303674  0.246760
1  bar    one  0.220157  0.961854
2  foo    two -1.181591  2.211784
3  bar  three -0.551541 -0.456083
4  foo    two -0.149208 -1.227642
5  bar    two  1.072285 -1.006910
6  foo    one  0.513676  1.716835
7  foo  three -1.517448  3.165538 

     A      B         C         D
1  bar    one  0.220157  0.961854
3  bar  three -0.551541 -0.456083
5  bar    two  1.072285 -1.006910
0  foo    one -1.303674  0.246760
2  foo    two -1.181591  2.211784
4  foo    two -0.149208 -1.227642
6  foo    one  0.513676  1.716835
7  foo  three -1.517448  3.165538 

     A      B         C         D
1  bar    one  0.220157  0.961854
3  bar  three -0.551541 -0.456083
5  bar    two  1.072285 -1.006910
0  foo    one -1.303674  0.246760
6  foo    one  0.513676  1.716835
7  foo  three -1.517448  3.165538
2  foo    two -1.181591  2.211784
4  foo    two -0.149208 -1.227642 

     A      B         C         D
0  foo    one -1.303674  0.246760
2  foo    two -1.181591  2.211784
4  foo    two -0.149208 -1.227642
6  foo    one  0.513676  1.716835
7  foo  three -1.517448  3.165538
1  bar    one  0.220157  0.961854
3  bar  three -0.551541 -0.456083
5  bar    two  1.072285 -1.006910 

     A      B         C         D
5  bar    two  1.072285 -1.006910
3  bar  three -0.551541 -0.456083
1  bar    one  0.220157  0.961854
2  foo    two -1.181591  2.211784
4  foo    two -0.149208 -1.227642
7  foo  three -1.517448  3.165538
0  foo    one -1.303674  0.246760
6  foo    one  0.513676  1.716835 

```

In [ ]:

```
# filering demo with a DataFrame
df = pd.DataFrame({'A' : ['foo', 'bar', 'foo', 'bar',
                            'foo', 'bar', 'foo', 'foo'],
                    'B' : ['one', 'one', 'two', 'three',
                            'two', 'two', 'one', 'three'],
                    'C' : np.random.randn(8),
                    'D' : np.random.randn(8)})

# filter rows where column A has value foo
print(df[df['A'] == 'foo'], '\n')

# filter rows where column A has value foo and column B has value one
print(df[(df['A'] == 'foo') & (df['B'] == 'one')], '\n')
```

```
     A      B         C         D
0  foo    one -0.786207  0.780677
2  foo    two  1.898877 -1.284035
4  foo    two  0.414662  0.076348
6  foo    one  1.503069  1.706267
7  foo  three  0.703213 -0.882494 

     A    B         C         D
0  foo  one -0.786207  0.780677
6  foo  one  1.503069  1.706267 

 

     A    B         C         D
0  foo  one -0.786207  0.780677
6  foo  one  1.503069  1.706267 

```

## describe function to get metrics[¶](#describe-function-to-get-metrics)

- Describe function gives you count, mean, sum, percentiles, etc. for numerical features.
    

In [ ]:

```
# describe demo with a DataFrame
df = pd.DataFrame({'A' : ['foo', 'bar', 'foo', 'bar',  
                            'foo', 'bar', 'foo', 'foo'],
                    'B' : ['one', 'one', 'two', 'three',
                            'two', 'two', 'one', 'three'],  
                    'C' : np.random.randn(8),
                    'D' : np.random.randn(8)})

# describe the DataFrame
print(df.describe(), '\n')

# percentiles 
print(df.describe(percentiles=[.05, .25, .5, .75, .95]), '\n')
```

```
              C         D
count  8.000000  8.000000
mean   0.611355 -0.273129
std    1.204481  1.155660
min   -0.442703 -1.925295
25%   -0.293939 -0.982377
50%    0.169433 -0.304303
75%    1.276295  0.420773
max    2.971910  1.453572 

              C         D
count  8.000000  8.000000
mean   0.611355 -0.273129
std    1.204481  1.155660
min   -0.442703 -1.925295
5%    -0.433037 -1.756459
25%   -0.293939 -0.982377
50%    0.169433 -0.304303
75%    1.276295  0.420773
95%    2.451324  1.262993
max    2.971910  1.453572 

```

## Converting dataframes into numpy matrices[¶](#Converting-dataframes-into-numpy-matrices)

In [ ]:

```
# convert a DataFrame to a numpy array
df = pd.DataFrame({'A' : ['foo', 'bar', 'foo', 'bar',
                            'foo', 'bar', 'foo', 'foo'],
                    'B' : ['one', 'one', 'two', 'three',
                            'two', 'two', 'one', 'three'],
                    'C' : np.random.randn(8),
                    'D' : np.random.randn(8)})

dum = pd.get_dummies(df)
print(dum, '\n')
martix = dum.values
print(martix, '\n')
```

```
          C         D  A_bar  A_foo  B_one  B_three  B_two
0 -0.622308 -0.492246      0      1      1        0      0
1 -0.534948 -0.047032      1      0      1        0      0
2  0.952138  2.265231      0      1      0        0      1
3 -0.886507  0.773916      1      0      0        1      0
4  0.139746 -3.616231      0      1      0        0      1
5  0.281794 -0.605569      1      0      0        0      1
6  0.600223  0.404806      0      1      1        0      0
7 -1.539877 -0.725982      0      1      0        1      0 

[[-0.62230795 -0.49224577  0.          1.          1.          0.
   0.        ]
 [-0.5349484  -0.04703176  1.          0.          1.          0.
   0.        ]
 [ 0.95213758  2.26523102  0.          1.          0.          0.
   1.        ]
 [-0.88650705  0.77391626  1.          0.          0.          1.
   0.        ]
 [ 0.13974649 -3.61623084  0.          1.          0.          0.
   1.        ]
 [ 0.28179357 -0.60556877  1.          0.          0.          0.
   1.        ]
 [ 0.60022346  0.40480551  0.          1.          1.          0.
   0.        ]
 [-1.53987732 -0.72598244  0.          1.          0.          1.
   0.        ]] 

```