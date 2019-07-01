---
---

## Exercises

===

### Exercise 1

Explore the use of `in` to test membership in a list. Create a list of
multiple integers, and use `in` to test membership of some other
numbers in your list.

[View solution](#solution-1)
{:.notes}

===

### Exercise 2

Based on what we have learned so far about lists and dictionaries,
think up a data structure suitable for an address book of names and
emails. Now create it! Enter the name and email address for yourself
and your neighbor in a new variable called `addr`.

[View solution](#solution-2)
{:.notes}

===

### Exercise 3

Write a for-loop that prints all even numbers between 1 and 9. Use the
modulo operator (`%`) to check for evenness: if `i` is even, then `i %
2` returns `0`, because `%` gives the remainder after division of the
first number by the second.

[View solution](#solution-3)
{:.notes}

===

### Exercise 4

Tune the `gamma` parameter for the Support Vector Machine from above
that used the `rbf` kernel method. It can take any postivie value.
Can you improve the confusion matrix? How does `gamma` appear to
affect the regions seen with `plot_decision_regions`? Does the
consuion matrix look okay out-of-sample (i.e. making predictions for
the counties not used for training)?

===

## Solutions

===

### Solution 1

```python
answers = [2, 15, 42, 19]
42 in answers
```

[Return](#exercise-1)
{:.notes}

===

### Solution 2

```python
addr = [
  {'name': 'Alice', 'email': 'alice@gmail.com'},
  {'name': 'Bob', 'email': 'bob59@aol.com'},
]
```

[Return](#exercise-1)
{:.notes}

===

### Solution 3

```python
for i in range(1, 9):
  if i % 2 == 0:
    print(i)
```

[Return](#exercise-3)
{:.notes}
