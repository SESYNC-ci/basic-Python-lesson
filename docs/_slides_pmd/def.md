---
---

## Function Definition

We already saw examples of a few built-in functions, such as `type()`
and `len()`.  New functions are defined as a block of code starting
with a `def` keyword and (optionally) finishing with a `return`.

```{python title='{{ site.handouts[0] }}'}
def add_two(x):
    result = x + 2
    return result
```

===

The `def` keyword is followed by the function name, its arguments enclosed in
parentheses (separated by commas if there are more than one), and a colon.

The `return` statement is needed to make the function provide output.
The lack of a `return`, or `return` followed by nothing, causes the function to return the value `None`.

===

```{python title='{{ site.handouts[0] }}'}
add_two(10)
```

This function is invoked by name followed by any arguments in
parentheses and **in the order defined**.

===

## Default arguments

A default value can be "assigned" during function definition.

```{python title='{{ site.handouts[0] }}'}
def add_any(x, y=0):
    result = x + y
    return result
```

===

Then the function can be called without that argument:

```{python title='{{ site.handouts[0] }}'}
add_any(10)
```

===

Adding an argument will override the default:

```{python title='{{ site.handouts[0] }}'}
add_any(10, 5)
```
