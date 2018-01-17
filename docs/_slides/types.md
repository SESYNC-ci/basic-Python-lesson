---
---




## Data types

The immutable data types are

| `'int'`   | Integer            |
| `'float'` | Real number        |
| `'str'`   | Character string   |
| `'bool'`  | `True`/`False`     |
| `'tuple'` | Immutable sequence |

===

Any object can be queried with `type()` 


~~~python
T = 'x', 3, True
type(T)
type('x')
~~~
{:.input}
~~~
Out[1]: str
~~~
{:.output}



===

## Operators

Python supports the usual arithmetic operators for numeric types:

| `+`  | addition                |
| `-`  | subtraction             |
| `*`  | multiplication          |
| `/`  | floating-point division |
| `**` | exponent                |
| `%`  | modulus                 |
| `//` | floor division          |

===

One or both of these might be a surprise:


~~~python
5 ** 2
~~~
{:.input}
~~~
Out[1]: 25
~~~
{:.output}




~~~python
2 // 3
~~~
{:.input}
~~~
Out[1]: 0
~~~
{:.output}



===

Some operators have natural extensions to non-numeric types:


~~~python
a * 2
~~~
{:.input}
~~~
Out[1]: 'xyzxyz'
~~~
{:.output}




~~~python
T + (3.14, 'y')
~~~
{:.input}
~~~
Out[1]: ('x', 3, True, 3.14, 'y')
~~~
{:.output}



===

Comparison operators are symbols or plain english:

| `==`       | equal                             |
| `!=`       | non-equal                         |
| `>`, `<`   | greater, lesser                   |
| `>=`, `<=` | greater or equal, lesser or equal |
| `and`      | logical and                       |
| `or`       | logical or                        |
| `not`      | logical negation                  |
| `in`       | logical membership                |

===

## Exercise 1

Explore the use of `in` to test membership in a list. Create a list of
multiple integers, and use `in` to test membership of some other
numbers in your list.

[View solution](#solution-1)
{:.notes}
