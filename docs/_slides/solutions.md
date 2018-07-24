---
---

## Exercises

===

### Exercise 1

Explore the use of `in` to test membership in a list. Create a list of
multiple integers, and use `in` to test membership of some other
numbers in your list.

[View solution](#solution-1)
{:.notes}

===

### Exercise 2

Based on what we have learned so far about lists and dictionaries,
think up a data structure suitable for an address book of names and
emails. Now create it! Enter the name and email address for yourself
and your neighbor in a new variable called `addr`.

[View solution](#solution-2)
{:.notes}

===

### Exercise 3

Write a for-loop that prints all even numbers between 1 and 9. Use the
modulo operator (`%`) to check for evenness: if `i` is even, then `i %
2` returns `0`, because `%` gives the remainder after division of the
first number by the second.

[View solution](#solution-3)
{:.notes}

===

## Solutions

===

### Solution 1


~~~python
answers = [2, 15, 42, 19]
42 in answers
~~~
{:.input title="Console"}
~~~
True
~~~
{:.output}



[Return](#exercise-1)
{:.notes}

===

### Solution 2


~~~python
addr = [
  {'name': 'Alice', 'email': 'alice@gmail.com'},
  {'name': 'Bob', 'email': 'bob59@aol.com'},
]
~~~
{:.input title="Console"}


[Return](#exercise-1)
{:.notes}

===

### Solution 3


~~~python
for i in range(1, 9):
  if i % 2 == 0:
    print(i)
~~~
{:.input title="Console"}
~~~
2
4
6
8
~~~
{:.output}



[Return](#exercise-3)
{:.notes}

===

### Solution 4


~~~
[0;31m---------------------------------------------------------------------------[0m
[0;31mFileNotFoundError[0m                         Traceback (most recent call last)
[0;32m<ipython-input-1-8895c54df491>[0m in [0;36m<module>[0;34m()[0m
[1;32m      1[0m [0;34m[0m[0m
[1;32m      2[0m [0;32mimport[0m [0mpandas[0m [0;32mas[0m [0mpd[0m[0;34m[0m[0m
[0;32m----> 3[0;31m [0manimals[0m [0;34m=[0m [0mpd[0m[0;34m.[0m[0mread_csv[0m[0;34m([0m[0;34m"data/animals.csv"[0m[0;34m)[0m[0;34m[0m[0m
[0m
[0;32m/usr/local/lib/python3.7/site-packages/pandas/io/parsers.py[0m in [0;36mparser_f[0;34m(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, squeeze, prefix, mangle_dupe_cols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, dayfirst, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, escapechar, comment, encoding, dialect, tupleize_cols, error_bad_lines, warn_bad_lines, skipfooter, doublequote, delim_whitespace, low_memory, memory_map, float_precision)[0m
[1;32m    676[0m                     skip_blank_lines=skip_blank_lines)
[1;32m    677[0m [0;34m[0m[0m
[0;32m--> 678[0;31m         [0;32mreturn[0m [0m_read[0m[0;34m([0m[0mfilepath_or_buffer[0m[0;34m,[0m [0mkwds[0m[0;34m)[0m[0;34m[0m[0m
[0m[1;32m    679[0m [0;34m[0m[0m
[1;32m    680[0m     [0mparser_f[0m[0;34m.[0m[0m__name__[0m [0;34m=[0m [0mname[0m[0;34m[0m[0m

[0;32m/usr/local/lib/python3.7/site-packages/pandas/io/parsers.py[0m in [0;36m_read[0;34m(filepath_or_buffer, kwds)[0m
[1;32m    438[0m [0;34m[0m[0m
[1;32m    439[0m     [0;31m# Create the parser.[0m[0;34m[0m[0;34m[0m[0m
[0;32m--> 440[0;31m     [0mparser[0m [0;34m=[0m [0mTextFileReader[0m[0;34m([0m[0mfilepath_or_buffer[0m[0;34m,[0m [0;34m**[0m[0mkwds[0m[0;34m)[0m[0;34m[0m[0m
[0m[1;32m    441[0m [0;34m[0m[0m
[1;32m    442[0m     [0;32mif[0m [0mchunksize[0m [0;32mor[0m [0miterator[0m[0;34m:[0m[0;34m[0m[0m

[0;32m/usr/local/lib/python3.7/site-packages/pandas/io/parsers.py[0m in [0;36m__init__[0;34m(self, f, engine, **kwds)[0m
[1;32m    785[0m             [0mself[0m[0;34m.[0m[0moptions[0m[0;34m[[0m[0;34m'has_index_names'[0m[0;34m][0m [0;34m=[0m [0mkwds[0m[0;34m[[0m[0;34m'has_index_names'[0m[0;34m][0m[0;34m[0m[0m
[1;32m    786[0m [0;34m[0m[0m
[0;32m--> 787[0;31m         [0mself[0m[0;34m.[0m[0m_make_engine[0m[0;34m([0m[0mself[0m[0;34m.[0m[0mengine[0m[0;34m)[0m[0;34m[0m[0m
[0m[1;32m    788[0m [0;34m[0m[0m
[1;32m    789[0m     [0;32mdef[0m [0mclose[0m[0;34m([0m[0mself[0m[0;34m)[0m[0;34m:[0m[0;34m[0m[0m

[0;32m/usr/local/lib/python3.7/site-packages/pandas/io/parsers.py[0m in [0;36m_make_engine[0;34m(self, engine)[0m
[1;32m   1012[0m     [0;32mdef[0m [0m_make_engine[0m[0;34m([0m[0mself[0m[0;34m,[0m [0mengine[0m[0;34m=[0m[0;34m'c'[0m[0;34m)[0m[0;34m:[0m[0;34m[0m[0m
[1;32m   1013[0m         [0;32mif[0m [0mengine[0m [0;34m==[0m [0;34m'c'[0m[0;34m:[0m[0;34m[0m[0m
[0;32m-> 1014[0;31m             [0mself[0m[0;34m.[0m[0m_engine[0m [0;34m=[0m [0mCParserWrapper[0m[0;34m([0m[0mself[0m[0;34m.[0m[0mf[0m[0;34m,[0m [0;34m**[0m[0mself[0m[0;34m.[0m[0moptions[0m[0;34m)[0m[0;34m[0m[0m
[0m[1;32m   1015[0m         [0;32melse[0m[0;34m:[0m[0;34m[0m[0m
[1;32m   1016[0m             [0;32mif[0m [0mengine[0m [0;34m==[0m [0;34m'python'[0m[0;34m:[0m[0;34m[0m[0m

[0;32m/usr/local/lib/python3.7/site-packages/pandas/io/parsers.py[0m in [0;36m__init__[0;34m(self, src, **kwds)[0m
[1;32m   1706[0m         [0mkwds[0m[0;34m[[0m[0;34m'usecols'[0m[0;34m][0m [0;34m=[0m [0mself[0m[0;34m.[0m[0musecols[0m[0;34m[0m[0m
[1;32m   1707[0m [0;34m[0m[0m
[0;32m-> 1708[0;31m         [0mself[0m[0;34m.[0m[0m_reader[0m [0;34m=[0m [0mparsers[0m[0;34m.[0m[0mTextReader[0m[0;34m([0m[0msrc[0m[0;34m,[0m [0;34m**[0m[0mkwds[0m[0;34m)[0m[0;34m[0m[0m
[0m[1;32m   1709[0m [0;34m[0m[0m
[1;32m   1710[0m         [0mpassed_names[0m [0;34m=[0m [0mself[0m[0;34m.[0m[0mnames[0m [0;32mis[0m [0;32mNone[0m[0;34m[0m[0m

[0;32mpandas/_libs/parsers.pyx[0m in [0;36mpandas._libs.parsers.TextReader.__cinit__[0;34m()[0m

[0;32mpandas/_libs/parsers.pyx[0m in [0;36mpandas._libs.parsers.TextReader._setup_parser_source[0;34m()[0m

[0;31mFileNotFoundError[0m: File b'data/animals.csv' does not exist
~~~
{:.output}




~~~python
(
animals
  .groupby('month')
  .agg({'id': 'count', 'weight': 'mean'})
  .rename({'id': 'n', 'weight': 'mean_weight'})
)
~~~
{:.input title="Console"}
~~~
[0;31m---------------------------------------------------------------------------[0m
[0;31mNameError[0m                                 Traceback (most recent call last)
[0;32m<ipython-input-1-408208f774f5>[0m in [0;36m<module>[0;34m()[0m
[1;32m      1[0m [0;34m[0m[0m
[1;32m      2[0m (
[0;32m----> 3[0;31m [0manimals[0m[0;34m[0m[0m
[0m[1;32m      4[0m   [0;34m.[0m[0mgroupby[0m[0;34m([0m[0;34m'month'[0m[0;34m)[0m[0;34m[0m[0m
[1;32m      5[0m   [0;34m.[0m[0magg[0m[0;34m([0m[0;34m{[0m[0;34m'id'[0m[0;34m:[0m [0;34m'count'[0m[0;34m,[0m [0;34m'weight'[0m[0;34m:[0m [0;34m'mean'[0m[0;34m}[0m[0;34m)[0m[0;34m[0m[0m

[0;31mNameError[0m: name 'animals' is not defined
~~~
{:.output}



[Return](#exercise-4)
{:.notes}
