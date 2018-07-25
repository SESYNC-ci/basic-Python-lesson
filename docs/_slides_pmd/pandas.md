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

```{python title='{{ site.handouts[0] }}'}
import pandas as pd
cbp = pd.read_csv('data/cbp15co.csv')
cbp.dtypes
```

[County Business Patterns (CBP)]: https://www.census.gov/programs-surveys/cbp/data/datasets.html

===

As is common with CSV files, the inferred data types were not quite right.

```{python title='{{ site.handouts[0] }}'}
cbp = pd.read_csv(
    'data/cbp15co.csv',
    dtype={'FIPSTATE':'str', 'FIPSCTY':'str'},
    )
cbp.dtypes
```

===

There are many ways to slice a `DataFrame`. To select a subset of rows
and/or columns by name, use the `loc` attribute and `[` for indexing.

```{python title='{{ site.handouts[0] }}'}
cbp.loc[:, ['FIPSTATE', 'NAICS']]
```

===

As with lists, `:` by itself indicates all the rows (or
columns). Unlike lists, the `loc` attribute returns both endpoints of
a slice.

```{python title='{{ site.handouts[0] }}'}
cbp.loc[2:4, 'FIPSTATE':'NAICS']
```

===

Use the `iloc` attribute of a DataFrame to get rows and/or columns by
position, which behaves identically to list indexing.

```{python title='{{ site.handouts[0] }}'}
cbp.iloc[2:4, 0:3]
```

===

The default indexing for a DataFrame, without using the `loc` or
`iloc` attributes, is by column name.

```{python title='{{ site.handouts[0] }}'}
cbp[['NAICS', 'AP']].head()
```

===

The `loc` attribute also allows logical indexing, i.e. the use of a
boolean array of appropriate length for the selected dimension. The
subset of `cbp` with sector level NAICS codes can indexed with string
matching.

```{python title='{{ site.handouts[0] }}'}
logical_idx = cbp['NAICS'].str.match('^[0-9]{2}----')
cbp = cbp.loc[logical_idx]
cbp.head()
```

===

Creation of new variables, our old favorite the full FIPS identifier,
is done by assignment to new column names, using another `str` method.

```{python title='{{ site.handouts[0] }}'}
cbp['FIPS'] = cbp['FIPSTATE'].str.cat(cbp['FIPSCTY'])
cbp.head()
```

===

## Index

The `DataFrame` object includes the notion of "primary keys" for a
table in its `Index` construct. One or more columns that uniquely
identify rows can be set aside from the remaining columns.

```{python title='{{ site.handouts[0] }}'}
cbp = cbp.set_index(['FIPS', 'NAICS'])
cbp.head()
```

===

Any hierarchical index can be "unstacked", and all columns appropriately spread into a "wide" table layout.

```{python title='{{ site.handouts[0] }}'}
cbp = cbp[['EMP', 'AP']].unstack(fill_value=0)
```

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

```{python title='{{ site.handouts[0] }}'}
income = cbp['EMP']
income = income.loc[:, ['11----', '72----']]
income.head()
```
