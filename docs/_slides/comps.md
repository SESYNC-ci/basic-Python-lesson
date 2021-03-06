---
---

## Iteration

The data structures just discussed have multiple values. Subsetting is
one way to get at them individually. Stepping through all values is
called iterating.

Python formally declares a thing "iterable" if it can be used in an
expression `for x in y`. where `y` is the iterable thing and `x` will
label each element in turn.

===

## Declarations with Iterables

Packing the `for x in y` expression inside a sequence declaration is
one way to build a sequence.


~~~python
letters = [x for x in 'abcde']
letters
~~~
{:.input title="Console"}
~~~
['a', 'b', 'c', 'd', 'e']
~~~
{:.output}



This way of declaring with `for` and `in` is called a "comprehension" in Python.

===

## Dictionary Comprehension

To declare a dictionary in this way, specify a `key:value` pair.


~~~python
CAPS = {x: x.upper() for x in 'abcde'}
CAPS
~~~
{:.input title="Console"}
~~~
{'a': 'A', 'b': 'B', 'c': 'C', 'd': 'D', 'e': 'E'}
~~~
{:.output}


