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
...          ...     ...
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
   FIPSTATE FIPSCTY   NAICS EMPFLAG  ... N1000_3  N1000_4 CENSTATE  CENCTY
1        01     001  11----     NaN  ...       0        0       63       1
10       01     001  21----     NaN  ...       0        0       63       1
17       01     001  22----     NaN  ...       0        0       63       1
27       01     001  23----     NaN  ...       0        0       63       1
93       01     001  31----     NaN  ...       0        0       63       1

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
   FIPSTATE FIPSCTY   NAICS EMPFLAG  ... N1000_4  CENSTATE CENCTY   FIPS
1        01     001  11----     NaN  ...       0        63      1  01001
10       01     001  21----     NaN  ...       0        63      1  01001
17       01     001  22----     NaN  ...       0        63      1  01001
27       01     001  23----     NaN  ...       0        63      1  01001
93       01     001  31----     NaN  ...       0        63      1  01001

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
             FIPSTATE FIPSCTY EMPFLAG  ... N1000_4  CENSTATE CENCTY
FIPS  NAICS                            ...                         
01001 11----       01     001     NaN  ...       0        63      1
      21----       01     001     NaN  ...       0        63      1
      22----       01     001     NaN  ...       0        63      1
      23----       01     001     NaN  ...       0        63      1
      31----       01     001     NaN  ...       0        63      1

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

