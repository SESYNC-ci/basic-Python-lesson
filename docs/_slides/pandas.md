---
---

## Pandas

If you have used the statistical programming language R, you are familiar with
"data frames", two-dimensional data structures where each column can hold a 
different type of data, as in a spreadsheet.

The analagous data frame package for Python is [pandas](){:.pylib},
which provides a `DataFrame` object type with methods to subset,
filter reshape and aggregate tabular data.

===

After importing [pandas](){:.pylib}, we call its `read_csv` function
to load the [County Business Patterns (CBP)] dataset.



~~~python
import pandas as pd
cbp = pd.read_csv('data/cbp15co.csv')
cbp.dtypes
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
FIPSTATE     int64
FIPSCTY      int64
NAICS       object
EMPFLAG     object
EMP_NF      object
EMP          int64
QP1_NF      object
QP1          int64
AP_NF       object
AP           int64
EST          int64
N1_4         int64
N5_9         int64
N10_19       int64
N20_49       int64
N50_99       int64
N100_249     int64
N250_499     int64
N500_999     int64
N1000        int64
N1000_1      int64
N1000_2      int64
N1000_3      int64
N1000_4      int64
CENSTATE     int64
CENCTY       int64
dtype: object
~~~
{:.output}


[County Business Patterns (CBP)]: https://www.census.gov/programs-surveys/cbp/data/datasets.html

===

As is common with CSV files, the inferred data types were not quite right.



~~~python
cbp = pd.read_csv(
    'data/cbp15co.csv',
    dtype={'FIPSTATE':'str', 'FIPSCTY':'str'},
    )
cbp.dtypes
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
FIPSTATE    object
FIPSCTY     object
NAICS       object
EMPFLAG     object
EMP_NF      object
EMP          int64
QP1_NF      object
QP1          int64
AP_NF       object
AP           int64
EST          int64
N1_4         int64
N5_9         int64
N10_19       int64
N20_49       int64
N50_99       int64
N100_249     int64
N250_499     int64
N500_999     int64
N1000        int64
N1000_1      int64
N1000_2      int64
N1000_3      int64
N1000_4      int64
CENSTATE     int64
CENCTY       int64
dtype: object
~~~
{:.output}


===

There are many ways to slice a `DataFrame`. To select a subset of rows
and/or columns by name, use the `loc` attribute and `[` for indexing.



~~~python
cbp.loc[:, ['FIPSTATE', 'NAICS']]
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
        FIPSTATE   NAICS
0             01  ------
1             01  11----
2             01  113///
3             01  1133//
4             01  11331/
5             01  113310
6             01  115///
7             01  1151//
8             01  11511/
9             01  115112
10            01  21----
11            01  212///
12            01  2123//
13            01  21231/
14            01  212319
15            01  21232/
16            01  212321
17            01  22----
18            01  221///
19            01  2211//
20            01  22111/
21            01  221112
22            01  22112/
23            01  221122
24            01  2213//
25            01  22131/
26            01  221310
27            01  23----
28            01  236///
29            01  2361//
...          ...     ...
2126571       56  611///
2126572       56  6113//
2126573       56  61131/
2126574       56  611310
2126575       56  6117//
2126576       56  61171/
2126577       56  611710
2126578       56  62----
2126579       56  621///
2126580       56  6213//
2126581       56  62134/
2126582       56  621340
2126583       56  6214//
2126584       56  62142/
2126585       56  621420
2126586       56  6216//
2126587       56  62161/
2126588       56  621610
2126589       56  6219//
2126590       56  62199/
2126591       56  621999
2126592       56  81----
2126593       56  812///
2126594       56  8129//
2126595       56  81299/
2126596       56  812990
2126597       56  813///
2126598       56  8133//
2126599       56  81331/
2126600       56  813312

[2126601 rows x 2 columns]
~~~
{:.output}


===

As with lists, `:` by itself indicates all the rows (or
columns). Unlike lists, the `loc` attribute returns both endpoints of
a slice.



~~~python
cbp.loc[2:4, 'FIPSTATE':'NAICS']
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
  FIPSTATE FIPSCTY   NAICS
2       01     001  113///
3       01     001  1133//
4       01     001  11331/
~~~
{:.output}


===

Use the `iloc` attribute of a DataFrame to get rows and/or columns by
position, which behaves identically to list indexing.



~~~python
cbp.iloc[2:4, 0:3]
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
  FIPSTATE FIPSCTY   NAICS
2       01     001  113///
3       01     001  1133//
~~~
{:.output}


===

The default indexing for a DataFrame, without using the `loc` or
`iloc` attributes, is by column name.



~~~python
cbp[['NAICS', 'AP']].head()
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
    NAICS      AP
0  ------  321433
1  11----    3566
2  113///    3551
3  1133//    3551
4  11331/    3551
~~~
{:.output}


===

The `loc` attribute also allows logical indexing, i.e. the use of a
boolean array of appropriate length for the selected dimension. The
subset of `cbp` with sector level NAICS codes can indexed with string
matching.



~~~python
logical_idx = cbp['NAICS'].str.match('[0-9]{2}----')
cbp = cbp.loc[logical_idx]
cbp.head()
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
   FIPSTATE FIPSCTY   NAICS EMPFLAG EMP_NF  EMP QP1_NF    QP1 AP_NF     AP  \
1        01     001  11----     NaN      H   70      H    790     H   3566   
10       01     001  21----     NaN      H   82      H    713     H   3294   
17       01     001  22----     NaN      H  196      H   4793     H  18611   
27       01     001  23----     NaN      G  372      G   2891     G  13801   
93       01     001  31----     NaN      H  971      H  15386     H  64263   

     ...    N100_249  N250_499  N500_999  N1000  N1000_1  N1000_2  N1000_3  \
1    ...           0         0         0      0        0        0        0   
10   ...           0         0         0      0        0        0        0   
17   ...           0         0         0      0        0        0        0   
27   ...           0         0         0      0        0        0        0   
93   ...           0         0         1      0        0        0        0   

    N1000_4  CENSTATE  CENCTY  
1         0        63       1  
10        0        63       1  
17        0        63       1  
27        0        63       1  
93        0        63       1  

[5 rows x 26 columns]
~~~
{:.output}


===

Creation of new variables, our old favorite the full FIPS identifier,
is done by assignment to new column names, using another `str` method.



~~~python
cbp['FIPS'] = cbp['FIPSTATE'].str.cat(cbp['FIPSCTY'])
cbp.head()
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
   FIPSTATE FIPSCTY   NAICS EMPFLAG EMP_NF  EMP QP1_NF    QP1 AP_NF     AP  \
1        01     001  11----     NaN      H   70      H    790     H   3566   
10       01     001  21----     NaN      H   82      H    713     H   3294   
17       01     001  22----     NaN      H  196      H   4793     H  18611   
27       01     001  23----     NaN      G  372      G   2891     G  13801   
93       01     001  31----     NaN      H  971      H  15386     H  64263   

    ...    N250_499  N500_999  N1000  N1000_1  N1000_2  N1000_3  N1000_4  \
1   ...           0         0      0        0        0        0        0   
10  ...           0         0      0        0        0        0        0   
17  ...           0         0      0        0        0        0        0   
27  ...           0         0      0        0        0        0        0   
93  ...           0         1      0        0        0        0        0   

    CENSTATE  CENCTY   FIPS  
1         63       1  01001  
10        63       1  01001  
17        63       1  01001  
27        63       1  01001  
93        63       1  01001  

[5 rows x 27 columns]
~~~
{:.output}


===

## Index

The `DataFrame` object includes the notion of "primary keys" for a
table in its `Index` construct. One or more columns that uniquely
identify rows can be set aside from the remaining columns.



~~~python
cbp = cbp.set_index(['FIPS', 'NAICS'])
cbp.head()
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
             FIPSTATE FIPSCTY EMPFLAG EMP_NF  EMP QP1_NF    QP1 AP_NF     AP  \
FIPS  NAICS                                                                    
01001 11----       01     001     NaN      H   70      H    790     H   3566   
      21----       01     001     NaN      H   82      H    713     H   3294   
      22----       01     001     NaN      H  196      H   4793     H  18611   
      23----       01     001     NaN      G  372      G   2891     G  13801   
      31----       01     001     NaN      H  971      H  15386     H  64263   

              EST   ...    N100_249  N250_499  N500_999  N1000  N1000_1  \
FIPS  NAICS         ...                                                   
01001 11----    7   ...           0         0         0      0        0   
      21----    3   ...           0         0         0      0        0   
      22----    9   ...           0         0         0      0        0   
      23----   75   ...           0         0         0      0        0   
      31----   24   ...           0         0         1      0        0   

              N1000_2  N1000_3  N1000_4  CENSTATE  CENCTY  
FIPS  NAICS                                                
01001 11----        0        0        0        63       1  
      21----        0        0        0        63       1  
      22----        0        0        0        63       1  
      23----        0        0        0        63       1  
      31----        0        0        0        63       1  

[5 rows x 25 columns]
~~~
{:.output}


===

Any hierarchical index can be "unstacked", and all columns appropriately spread into a "wide" table layout.



~~~python
cbp = cbp[['EMP', 'AP']].unstack(fill_value=0)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


The last transformation kept only two variables for each FIPS and
NAICS combination: the number of employees and the annual payroll (x
$1000). By now, it may be obvious we are slowly working towards some
goal!
{:.notes}

===

The number of employees in just two sectors will serve as the set of
variables (i.e. columns) by which we attempt to classify each county
as "Metro" (i.e. urban) or not (i.e. rural). The first code is for
Agriculture, Forestry, Fishing, and Hunting. The second is
Accommodation and Food Services.



~~~python
employment = cbp['EMP']
employment = employment.loc[:, ['11----', '72----']]
employment.head()
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
NAICS  11----  72----
FIPS                 
01001      70    2091
01003      14   12081
01005     180     594
01007      70     306
01009      10     679
~~~
{:.output}

