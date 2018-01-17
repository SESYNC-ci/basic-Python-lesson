---
---

## Data structures

The built-in structures for holding multiple values are:

- Tuple
- List
- Set
- Dictionary

===

## Tuple

The simplest kind of sequence, a tuple is declared with
comma-separated values, optionally inside `()`.


~~~python
T = 'x', 3, True
type(T)
~~~
{:.input}
~~~
Out[1]: tuple
~~~
{:.output}



Note that to declare a one-tuple without "(", a trailing "," is required.


~~~python
T = 'cat',
type(T)
~~~
{:.input}
~~~
Out[1]: tuple
~~~
{:.output}



===

## List

The more common kind of sequence in Python is the list, which is
declared with comma-separated values inside `[]`. Unlike a tuple, a
list is mutable.


~~~python
L = [3.14, 'xyz', T]
type(L)
~~~
{:.input}
~~~
Out[1]: list
~~~
{:.output}



===

## Subsetting Tuples and Lists

Subsetting elements from a tuple or list is performed with square
brackets in both cases, and selects elements using their integer
position starting from zero---their "index".


~~~python
L[0]
~~~
{:.input}
~~~
Out[1]: 3.14
~~~
{:.output}



===

Negative indices are allowed, and refer to the reverse ordering: -1 is
the last item in the list, -2 the second-to-last item, and so on.


~~~python
L[-1]
~~~
{:.input}
~~~
Out[1]: ('cat',)
~~~
{:.output}



===

The syntax `L[i:j]` selects a sub-list starting with the element at index
`i` and ending with the element at index `j - 1`.


~~~python
L[0:2]
~~~
{:.input}
~~~
Out[1]: [3.14, 'xyz']
~~~
{:.output}



A blank space before or after the ":" indicates the start or end of the list,
respectively. For example, the previous example could have been written 
`L[:2]`.

===

A potentially useful trick to remember the list subsetting rules in Python is
to picture the indices as "dividers" between list elements.

~~~
 0      1       2          3 
 | 3.14 | 'xyz' | ('cat',) |
-3     -2      -1
~~~
{:.input}

Positive indices are written at the top and negative indices at the bottom. 
`L[i]` returns the element to the right of `i` whereas `L[i:j]` returns
elements between `i` and `j`.

===

## Set

The third and last "sequence" data structure is a set, used mainly for quick access to set operations like "union" and "difference". Declare a set with comma-separated values inside `{}` or by casting another sequence with `set()`.


~~~python
S1 = set(L)
S2 = {3.14, 'z'}
S1.difference(S2)
~~~
{:.input}
~~~
Out[1]: {('cat',), 'xyz'}
~~~
{:.output}



Python is a rather principled language: a set is technically unordered, so its elements do not have an index. You cannot subset a set using `[]`.
{:.notes}

===

## Dictionary

Lists are useful when you need to access elements by their position in
a sequence. In contrast, a dictionary is needed to find values based
on arbitrary identifiers.

===

Construct a dictionary with comma-separated `key: value` pairs in `{}`.


~~~python
toons = {
  'Snowy': 'dog',
  'Garfield': 'cat',
  'Bugs': 'bunny',
}
type(toons)
~~~
{:.input}
~~~
Out[1]: dict
~~~
{:.output}



===

Individual values are accessed using square brackets, as for lists,
but the key must be used rather than an index.


~~~python
toons['Bugs']
~~~
{:.input}
~~~
Out[1]: 'bunny'
~~~
{:.output}



===

To add a single new element to the dictionary, define a new
`key:value` pair by assigning a value to a novel key in the
dictionary.


~~~python
toons['Goofy'] = 'dog'
toons
~~~
{:.input}
~~~
Out[1]: {'Bugs': 'bunny', 'Garfield': 'cat', 'Goofy': 'dog', 'Snowy': 'dog'}
~~~
{:.output}



Dictionary keys are unique. Assigning a value to an existing key
overwrites its previous value.

===

## Exercise 2

Based on what we have learned so far about lists and dictionaries,
think up a data structure suitable for an address book of names and
emails. Now create it! Enter the name and email address for yourself
and your neighbor in a new variable called `addr`.

[View solution](#solution-2)
{:.notes}
