---
---

## Methods

The period is a special character in Python that accesses an object's
attributes and methods. In either the Jupyter Notebook or Console,
typing an object's name followed by `.` and then pressing the `TAB`
key brings up suggestions.



~~~python
squares.index(4)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
1
~~~
{:.output}


===

We call this `index()` function a method of lists (recall that
`squares` is of type `'list'`). A useful feature of having methods
attached to objects is that their documentation is attached too.



~~~python
> help(squares.index)
~~~
{:title="Console" .input}


~~~
Help on built-in function index:

index(...)
    L.index(value, [start, [stop]]) -> integer -- return first index of value.
    Raises ValueError if the value is not present.
~~~
{:.output}


A major differnce between Python and R has to do with the process for
making functions behave differently for different objects. In Python,
a function is attached to an object as a "method", while in R it is
common for a "dispatcher" to examine the attributes of a function
call's arguments and chooses the particular function to use.
{:.notes}

===

Dictionary's have an `update()` method, for merging the contents
of a second dictionary into the one calling `update()`.



~~~python
user.update({
  'Nickname': 'Jamie',
  'Age': 24,
})
user
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


~~~
{'First Name': 'J.', 'Last Name': 'Doe', 'Age': 24, 'Nickname': 'Jamie', 'Email': 'j.doe@gmail.com'}
~~~
{:.output}


===

Note a couple "Pythonic" style choices in the above:

1. Leave a space after the `:` when declaring `key: value` pairs
1. Trailing null arguments are syntactically correct, even advantageous
1. White space within `(...)` has no meaning and can improve readiability

The "style-guide" for Python scripting, [PEP 8], is first authored by the inventor
of Python and adhered too by many. It's sometimes nice to know their is a preferred
way of writing code, but don't let it be a burden.
{:.notes}

[PEP 8]: https://www.python.org/dev/peps/pep-0008/
