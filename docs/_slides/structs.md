---
---

## Data Structures

The built-in structures for holding multiple values are:

- Tuple
- List
- Set
- Dictionary

===

## Tuple

The simplest kind of sequence, a tuple is declared with
comma-separated values, optionally inside `(...)`. The tuple is a
common type of return value for functions with multiple outputs.



~~~python
T = 'x', 3, True
type(T)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
<class 'tuple'>
~~~
{:.output}


===

To declare a one-tuple without `(...)`, a trailing "," is required.



~~~python
T = 'cat',
type(T)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
<class 'tuple'>
~~~
{:.output}


===

## List

The more common kind of sequence in Python is the list, which is
declared with comma-separated values inside `[...]`. Unlike a tuple, a
list is mutable.



~~~python
L = [3.14, 'xyz', T]
type(L)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
<class 'list'>
~~~
{:.output}


===

## Subsetting Tuples and Lists

Subsetting elements from a tuple or list is performed with square
brackets in both cases, and selects elements using their integer
position starting from zero---their "index".



~~~python
> L[0]
~~~
{:title="Console" .input}


~~~
3.14
~~~
{:.output}


===

Negative indices are allowed, and refer to the reverse ordering: -1 is
the last item in the list, -2 the second-to-last item, and so on.



~~~python
> L[-1]
~~~
{:title="Console" .input}


~~~
('cat',)
~~~
{:.output}


===

The syntax `L[i:j]` selects a sub-list starting with the element at index
`i` and ending with the element at index `j - 1`.



~~~python
> L[0:2]
~~~
{:title="Console" .input}


~~~
[3.14, 'xyz']
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

Positive indices are written at the top and negative indices at the bottom. 
`L[i]` returns the element to the right of `i` whereas `L[i:j]` returns
elements between `i` and `j`.
{:.notes}

===

## Set

The third and last "sequence" data structure is a set, useful for
operations like "union" and "difference". Declare a set with
comma-separated values inside `{...}` or by casting another sequence with
`set()`.



~~~python
S1 = set(L)
S2 = {3.14, 'z'}
S1.difference(S2)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
{'xyz', ('cat',)}
~~~
{:.output}


Python is a rather principled language: a set is technically
unordered, so its elements do not have an index. You cannot subset a
set using `[...]`.
{:.notes}

===

## Dictionary

Lists are useful when you need to access elements by their position in
a sequence. In contrast, a dictionary is needed to find values based
on arbitrary identifiers, called "keys".

===

Construct a dictionary with comma-separated `key: value` pairs within `{...}`.



~~~python
user = {
  'First Name': 'J.',
  'Last Name': 'Doe',
  'Email': 'j.doe@gmail.com',
}
type(user)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
<class 'dict'>
~~~
{:.output}


===

Individual values are accessed using square brackets, as for lists,
but the key must be used rather than an index.



~~~python
user['Email']
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
'j.doe@gmail.com'
~~~
{:.output}


===

To add a single new element to the dictionary, define a new
`key:value` pair by assigning a value to a novel key in the
dictionary.



~~~python
user['Age'] = 42
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


Dictionary keys are unique. Assigning a value to an existing key
overwrites its previous value. You would replace the current Gmail
address with `user['Email'] = doedoe1337@aol.com`.
{:.notes}
