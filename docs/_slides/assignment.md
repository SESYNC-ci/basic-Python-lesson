---
---

## Variables

Variable assignment attaches the label left of an `=` to the return
value of the expression on its right.


~~~python
a = 'xyz'
a
~~~
{:.text-document title="{{ site.handouts[0] }}"}

~~~
'xyz'
~~~
{:.output}



Colloquially, you might say the new variable `a` equals `'xyz'`, but
Python makes it easy to "go deeper". There can be only one string
`'xyz'`, so the Python interpreter makes `a` into another label for
the same `'xyz'`, which we can verify by `id()`.
{:.notes}

===

The "in-memory" location of `a` returned by `id()` ...


~~~python
id(a)
~~~
{:.input title="Console"}
~~~
4454018216
~~~
{:.output}



... is equal to that of `xyz` itself:


~~~python
id('xyz')
~~~
{:.input title="Console"}
~~~
4454018216
~~~
{:.output}



===

The idiom to test this "sameness" is typical of the Python language:
it uses plain English when words will suffice.


~~~python
a is 'xyz'
~~~
{:.input title="Console"}
~~~
True
~~~
{:.output}



===

## Equal but not the Same

The `id()` function helps demonstrate that "equal" is not the "same".


~~~python
b = [1, 2, 3]
id(b)
~~~
{:.text-document title="{{ site.handouts[0]}}"}

~~~
4443177480
~~~
{:.output}




~~~python
id([1, 2, 3])
~~~
{:.input title="Console"}
~~~
4445161480
~~~
{:.output}



===

Even though `b == [1, 2, 3]` returns `True`, these are not the same
object:


~~~python
b is [1, 2, 3]
~~~
{:.input title="Console"}
~~~
False
~~~
{:.output}



===

## Side-effects

The reason to be aware of what `b` **is** has to do with
"side-effects", an very import part of Python programming. A
side-effect occurs when an expression generates some ripples other
than its return value.


~~~python
b.pop()
b
~~~
{:.input title="Console"}
~~~
[1, 2]
~~~
{:.output}



Python is an object-oriented language from the ground up---everything
is an "object" with some state to be more or less aware of. And
side-effects don't touch the label, they effect what the label is
assigned to (i.e. what it **is**).
{:.notes}

===

Question
: Re-check the "in-memory" location---is it the same `b`?

Answer
: {:.fragment} Yes! The list got shorter but it is the same list.

===

Side-effects trip up Python programmers when an object has multiple
labels, which is not so unusual:


~~~python
c = b
b.pop()
~~~
{:.text-document title="{{ site.handouts[0] }}"}




~~~python
c
~~~
{:.input title="Console"}
~~~
[1]
~~~
{:.output}



The assignment to `c` does not create a new list, so the side-effect
of popping off the tail of `b` ripples into `c`.

A common mistake for those coming to Python from R, is to write `b =
b.append(4)`, which overwrites `b` with the value `None` that happens
to be returned by the `append()` method.
{:.notes}

<!--
===

Not every object is "mutable" like our list `b`. For example, the `a`
assigned earlier is not.


~~~python
x = a
a.upper()
~~~
{:.input title="Console"}
~~~
'XYZ'
~~~
{:.output}



===


~~~python
x
~~~
{:.input title="Console"}
~~~
'xyz'
~~~
{:.output}



The string 'xyz' hasn't changed---it's immutable. So it is also a safe
guess that there has been no side-effect on the original `a`.


~~~python
a
~~~
{:.input title="Console"}
~~~
'xyz'
~~~
{:.output}


-->
