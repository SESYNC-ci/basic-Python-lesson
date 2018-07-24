---
---



## Function definition

We already saw examples of a few built-in functions, such as `type()`
and `len()`.  New functions are defined as a block of code starting
with a `def` keyword and (optionally) finishing with a `return`.


~~~python
def add_two(x):
    result = x + 2
    return result
~~~
{:.input title="Console"}


===

The `def` keyword is followed by the function name, its arguments enclosed in
parentheses (separated by commas if there are more than one), and a colon.

The `return` statement is needed to make the function provide output.
The lack of a `return`, or `return` followed by nothing, causes the function to return the value `None`.

===


~~~python
add_two(10)
~~~
{:.input title="Console"}
~~~
12
~~~
{:.output}



This function is invoked by name followed by any arguments in
parentheses and **in the order defined**.

===

## Default arguments

A default value can be "assigned" during function definition.


~~~python
def add_any(x, y=0):
    result = x + y
    return result
~~~
{:.input title="Console"}


===

Then the function can be called without that argument:


~~~python
add_any(10)
~~~
{:.input title="Console"}
~~~
10
~~~
{:.output}



===

Adding an argument will override the default:


~~~python
add_any(10, 5)
~~~
{:.input title="Console"}
~~~
15
~~~
{:.output}



===

## Methods

The period is a special character in Python that accesses an object's
attributes and methods. In either the Jupyter Notebook or Console,
typing an object's name followed by `.` and then pressing the `TAB`
key brings up suggestions.


~~~python
squares.index(4)
~~~
{:.input title="Console"}


===

We call this `index()` function a method of lists (recall that
`squares` is of type `'list'`). A useful feature of having methods
attached to objects is that we can dial up help on a method as it
applies to any instance of a type.


~~~python
help(squares.index)
~~~
{:.input title="Console"}
~~~
Help on built-in function index:

index(value, start=0, stop=9223372036854775807, /) method of builtins.list instance
    Return first index of value.
    
    Raises ValueError if the value is not present.

~~~
{:.output}



A major differnce between Python and R has to do with the process for making functions behave differently for different objects. In Python, a function is attached to an object as a "method", while in R a "dispatcher" examines the attributes of a function call's arguments and chooses a the particular function to use.
{:.notes}

===

## A dictionary method

The `update()` method allows you to extend a dictionary with another dictionary of `key:value` pairs, while simultaneously overwriting values for existing keys.


~~~python
toons.update({
  'Tweety': 'bird',
  'Bob': 'sponge',
  'Bugs': 'rabbit',
})
~~~
{:.input title="Console"}
~~~
[0;31m---------------------------------------------------------------------------[0m
[0;31mNameError[0m                                 Traceback (most recent call last)
[0;32m<ipython-input-1-2cd87e484c55>[0m in [0;36m<module>[0;34m()[0m
[1;32m      1[0m [0;34m[0m[0m
[0;32m----> 2[0;31m toons.update({
[0m[1;32m      3[0m   [0;34m'Tweety'[0m[0;34m:[0m [0;34m'bird'[0m[0;34m,[0m[0;34m[0m[0m
[1;32m      4[0m   [0;34m'Bob'[0m[0;34m:[0m [0;34m'sponge'[0m[0;34m,[0m[0;34m[0m[0m
[1;32m      5[0m   [0;34m'Bugs'[0m[0;34m:[0m [0;34m'rabbit'[0m[0;34m,[0m[0;34m[0m[0m

[0;31mNameError[0m: name 'toons' is not defined
~~~
{:.output}



===

Question
: How many `key: value` pairs are there now in toons?

Answer
: {:.fragment} Five. The key `'Bugs'` is only inserted once.

===

Note a couple "Pythonic" style choices of the above:

1. Leave a space after the `:` when declaring `key: value` pairs
1. Trailing null arguments are syntactically correct, even advantageous
1. White space with `()` has no meaning and can improve readiability
