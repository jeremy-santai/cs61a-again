# 2.2 Data Abstraction

Most real-world objects have compound structure. For instance, geographic positions combine latitude and longitude coordinates. Programming languages need the ability to couple multiple values together as a single unit while still allowing individual access to each component.

This approach, called **data abstraction**, separates how data is represented from how it is manipulated. "The general technique of isolating the parts of a program that deal with how data are represented from the parts that deal with how data are manipulated is a powerful design methodology called _data abstraction_."

## 2.2.1 Example: Rational Numbers

Rational numbers (fractions like 1/3 or 17/29) require exact representation. Direct division produces approximations:

```python
>>> 1/3
0.3333333333333333
```

The strategy involves assuming three functions exist before implementing them:

- `rational(n, d)` constructs a rational number
- `numer(x)` returns the numerator
- `denom(x)` returns the denominator

Using these, we can build operations without knowing the underlying representation:

```python
def add_rationals(x, y):
    nx, dx = numer(x), denom(x)
    ny, dy = numer(y), denom(y)
    return rational(nx * dy + ny * dx, dx * dy)

def mul_rationals(x, y):
    return rational(numer(x) * numer(y), denom(x) * denom(y))

def print_rational(x):
    print(numer(x), '/', denom(x))

def rationals_are_equal(x, y):
    return numer(x) * denom(y) == numer(y) * denom(x)
```

## 2.2.2 Pairs

Python lists serve as compound structures. Two-element lists can be created and accessed:

```python
>>> pair = [10, 20]
>>> x, y = pair
>>> x
10
>>> pair[0]
10
```

For rational numbers, we implement:

```python
def rational(n, d):
    return [n, d]

def numer(x):
    return x[0]

def denom(x):
    return x[1]
```

Initially, this produces unreduced fractions (6/9 instead of 2/3). Using the greatest common divisor function improves the constructor:

```python
from fractions import gcd

def rational(n, d):
    g = gcd(n, d)
    return (n//g, d//g)
```

The floor division operator `//` performs integer division. This modification demonstrates how changing the constructor alone, without altering arithmetic operations, refines behavior.

## 2.2.3 Abstraction Barriers

Data abstraction divides programs into layers with defined boundaries:

| **Program Section** | **Data View** | **Operations** |
|---|---|---|
| Computation with rationals | Whole values | add_rational, mul_rational, etc. |
| Creating/implementing rationals | Numerators and denominators | rational, numer, denom |
| Selector/constructor implementation | Two-element lists | List operations |

An **abstraction barrier violation** occurs when code bypasses higher-level functions. For example:

```python
# Correct: uses mul_rational
def square_rational(x):
    return mul_rational(x, x)

# Violates barrier: accesses numer/denom directly
def square_rational_violating_once(x):
    return rational(numer(x) * numer(x), denom(x) * denom(x))

# Violates barrier twice: accesses list structure
def square_rational_violating_twice(x):
    return [x[0] * x[0], x[1] * x[1]]
```

The first implementation remains valid if rational representation changes; the others require updates.

## 2.2.4 The Properties of Data

Abstract data is defined by behavior conditions rather than specific implementations. For rational numbers, the key relationship is: "if we construct a rational number x from integers n and d, then it should be the case that numer(x)/denom(x) is equal to n/d."

Pairs require only one behavior condition: if constructed from values x and y, selecting index 0 returns x and selecting index 1 returns y.

Surprisingly, pairs can be implemented using functions instead of lists:

```python
def pair(x, y):
    """Return a function that represents a pair."""
    def get(index):
        if index == 0:
            return x
        elif index == 1:
            return y
    return get

def select(p, i):
    """Return the element at index i of pair p."""
    return p(i)
```

This demonstrates that "Functions are sufficient to represent compound data." Data abstraction allows switching between representations as long as behavior conditions are maintained.


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
