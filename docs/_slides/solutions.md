---
---

## Exercise solutions

===

## Solution 1


~~~python
answers = [2, 15, 42, 19]
42 in answers
~~~
{:.input}
~~~
Out[1]: True
~~~
{:.output}



[Return](#exercise-1)
{:.notes}

===

## Solution 2


~~~python
addr = [
  {'name': 'Alice', 'email': 'alice@gmail.com'},
  {'name': 'Bob', 'email': 'bob59@aol.com'},
]
~~~
{:.input}


[Return](#exercise-1)
{:.notes}

===

## Solution 3


~~~python
for i in range(1, 9):
  if i % 2 == 0:
    print(i)
~~~
{:.input}
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

## Solution 4





~~~python
(
animals
  .groupby('month')
  .agg({'id': 'count', 'weight': 'mean'})
  .rename({'id': 'n', 'weight': 'mean_weight'})
)
~~~
{:.input}
~~~
Out[1]: 
         id     weight
month                 
1      2518  41.656815
2      2796  40.569822
3      3390  42.558372
4      3443  45.290231
5      3073  46.651155
6      2697  41.161753
7      3633  39.923124
8      2369  42.575729
9      2751  43.830675
10     3064  43.879402
11     3016  43.046996
12     2799  40.408385
~~~
{:.output}



[Return](#exercise-4)
{:.notes}
