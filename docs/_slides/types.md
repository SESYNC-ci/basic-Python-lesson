---
---

## Data Types

The basic data types are

| `'int'`      | integers            |
| `'float'`    | real numbers        |
| `'str'`      | character strings   |
| `'bool'`     | `True` or `False`   |
| `'NoneType'` | `None`              |

===

Any object can be queried with `type()` 



~~~python
type('x')
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
<type 'str'>
~~~
{:.output}


===

## Operators

Python supports the usual (or not) arithmetic operators for numeric types:

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
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
25
~~~
{:.output}




~~~python
2 // 3
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
0
~~~
{:.output}


===

Some operators have natural extensions to non-numeric types:



~~~python
a * 2
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
'xyzxyz'
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
