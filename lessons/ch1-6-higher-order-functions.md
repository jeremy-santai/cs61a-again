# 1.6 Higher-Order Functions

"Functions that manipulate functions are called higher-order functions" and they serve as powerful abstraction mechanisms.

## 1.6.1 Functions as Arguments

Three functions that share a common pattern: `sum_naturals`, `sum_cubes`, and `pi_sum`. Rather than duplicating code, the underlying pattern can be abstracted into a general `summation` function:

```python
def summation(n, term):
    total, k = 0, 1
    while k <= n:
        total, k = total + term(k), k + 1
    return total
```

This allows functions like `cube` or `identity` to be passed as arguments, enabling reuse of the summation logic.

## 1.6.2 Functions as General Methods

The `improve` function demonstrates a general iterative refinement algorithm:

```python
def improve(update, close, guess=1):
    while not close(guess):
        guess = update(guess)
    return guess
```

This computes the golden ratio by accepting update and validation functions as parameters, showing how higher-order functions express general computational methods independent of specific implementations.

## 1.6.3 Nested Definitions

Nested function definitions address namespace clutter and function signature constraints. The `sqrt` function demonstrates this:

```python
def sqrt(a):
    def sqrt_update(x):
        return average(x, a/x)
    def sqrt_close(x):
        return approx_eq(x * x, a)
    return improve(sqrt_update, sqrt_close)
```

**Key concept—lexical scoping**: "Locally defined functions have access to the name bindings in the scope in which they are defined." Inner functions access the parent environment where they were defined, not where they're called.

The environment model requires two extensions:
- Each user-defined function has a parent environment
- A function's local frame extends its parent environment

Functions that "enclose" information from their definition environment are called **closures**.

## 1.6.4 Functions as Returned Values

Functions can return other functions. The `compose1` example shows function composition:

```python
def compose1(f, g):
    def h(x):
        return f(g(x))
    return h
```

Lexically scoped languages maintain the parent environment when returning locally defined functions.

## 1.6.5 Newton's Method

Newton's method finds zeros of differentiable functions through iterative improvement. A `newton_update` function follows tangent lines:

```python
def newton_update(f, df):
    def update(x):
        return x - f(x) / df(x)
    return update
```

This enables computing roots of arbitrary degree, such as square roots and cube roots, by finding zeros of polynomial equations.

## 1.6.6 Currying

Currying transforms multi-argument functions into chains of single-argument functions. A curried power function:

```python
def curried_pow(x):
    def h(y):
        return pow(x, y)
    return h
```

allows `curried_pow(2)(3)` to compute 2³. Helper functions automate this:

```python
def curry2(f):
    def g(x):
        def h(y):
            return f(x, y)
        return h
    return g
```

## 1.6.7 Lambda Expressions

Lambda expressions create unnamed functions. The syntax is:

```python
lambda x: f(g(x))
```

which reads as "a function that takes x and returns f(g(x))". Example:

```python
s = lambda x: x * x
```

While more concise than `def` statements, "compound lambda expressions are notoriously illegible, despite their brevity." Python style generally prefers explicit `def` statements.

## 1.6.8 Abstractions and First-Class Functions

Functions in Python have full first-class status, meaning they can be:
1. Bound to names
2. Passed as arguments to functions
3. Returned as function results
4. Included in data structures

This enables powerful abstraction and composition patterns.

## 1.6.9 Function Decorators

Decorators apply higher-order functions to `def` statements using `@` syntax:

```python
@trace
def triple(x):
    return 3 * x
```

This is equivalent to `triple = trace(triple)`. The decorator runs the higher-order function on the newly defined function and binds the result to the original name.


---

## Same Chapter

- [Ch1 1 Getting Started](ch1-1-getting-started.md)
- [Ch1 2 Elements Of Programming](ch1-2-elements-of-programming.md)
- [Ch1 3 Defining New Functions](ch1-3-defining-new-functions.md)
- [Ch1 4 Designing Functions](ch1-4-designing-functions.md)
- [Ch1 5 Control](ch1-5-control.md)
- [Ch1 7 Recursive Functions](ch1-7-recursive-functions.md)
