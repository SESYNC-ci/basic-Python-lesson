---
---

## Data Types

The basic data types are

| `'int'`   | Integer            |
| `'float'` | Real number        |
| `'str'`   | Character string   |
| `'bool'`  | `True`/`False`     |
| `'tuple'` | Immutable sequence |

===

Any object can be queried with `type()` 

```{python title='{{ site.handouts[0] }}'}
T = 'x', 3, True
type(T)
type('x')
```

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

```{python title='{{ site.handouts[0] }}'}
5 ** 2
```

```{python title='{{ site.handouts[0] }}'}
2 // 3
```

===

Some operators have natural extensions to non-numeric types:

```{python title='{{ site.handouts[0] }}'}
a * 2
```

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
