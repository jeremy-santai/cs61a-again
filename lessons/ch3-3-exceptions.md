# 3.3 Exceptions

This section explores how programmers can manage errors through exception handling. "There is no single correct approach to handling errors in a program," as different applications require different strategies—from web servers that log errors while continuing operation to interpreters that terminate immediately.

## Raising Exceptions

An exception is "an object instance with a class that inherits, either directly or indirectly, from the BaseException class." Programmers can raise exceptions using the `raise` statement:

```python
>>> raise Exception('An error occurred')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
Exception: an error occurred
```

When raised, no further statements execute in the current block unless the exception is handled.

## Handling Exceptions

A `try` statement manages exceptions through this structure:

```python
try:
    <try suite>
except <exception class> as <name>:
    <except suite>
```

Example demonstrating exception handling:

```python
>>> try:
        x = 1/0
    except ZeroDivisionError as e:
        print('handling a', type(e))
        x = 0
handling a <class 'ZeroDivisionError'>
```

## 3.3.1 Exception Objects

Custom exception classes can store additional information. The section demonstrates creating `IterImproveError` to preserve the last guess during iterative improvement when errors occur:

```python
class IterImproveError(Exception):
    def __init__(self, last_guess):
        self.last_guess = last_guess
```

This approach allows separating "iterative improvement logic from error handling logic," enhancing modularity in program design.


---

## Same Chapter

- [Ch3 1 Introduction](ch3-1-introduction.md)
- [Ch3 2 Functional Programming](ch3-2-functional-programming.md)
- [Ch3 4 Interpreters Combination](ch3-4-interpreters-combination.md)
- [Ch3 5 Interpreters Abstraction](ch3-5-interpreters-abstraction.md)
