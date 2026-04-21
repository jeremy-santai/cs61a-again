# 1.2 Elements of Programming

A programming language serves as both a tool for instructing computers and a framework for organizing ideas about computational processes. Programs communicate these ideas within programming communities, making it essential that code be written for human comprehension first.

## Three Core Mechanisms

Every powerful programming language provides three key mechanisms:

- **Primitive expressions and statements** — the simplest building blocks
- **Means of combination** — methods for constructing compound elements from simpler ones
- **Means of abstraction** — ways to name and manipulate compound elements as units

Programming involves two kinds of elements: functions and data.

## 1.2.1 Expressions

Primitive expressions begin with numbers:

```python
>>> 42
42
```

Mathematical operators combine expressions into compounds:

```python
>>> -1 - -1
0
>>> 1/2 + 1/4 + 1/8 + 1/16 + 1/32 + 1/64 + 1/128
0.9921875
```

Python uses *infix notation*, where operators appear between operands.

## 1.2.2 Call Expressions

The most important compound expression type is a *call expression*, applying a function to arguments:

```python
>>> max(7.5, 9.5)
9.5
```

The operator (function name) precedes parentheses enclosing comma-delimited operands.

Functions may accept arbitrary argument numbers:

```python
>>> max(1, -2, 3, -4)
3
```

Nested call expressions work straightforwardly:

```python
>>> max(min(1, -2), min(pow(3, 5), -4))
-2
```

## 1.2.3 Importing Library Functions

Python organizes functions into modules comprising the Python Library. Import statements make these available:

```python
>>> from math import sqrt
>>> sqrt(256)
16.0
```

The operator module provides function equivalents for infix operators:

```python
>>> from operator import add, sub, mul
>>> add(14, 28)
42
>>> sub(100, mul(7, add(8, 4)))
16
```

## 1.2.4 Names and the Environment

Names bind to values through assignment statements:

```python
>>> radius = 10
>>> radius
10
>>> 2 * radius
20
```

Names also bind through import statements:

```python
>>> from math import pi
>>> pi * 71 / 223
1.0002380197528042
```

The assignment operator (=) provides abstraction. An *environment* maintains the memory tracking names, values, and bindings.

Names can bind to functions:

```python
>>> f = max
>>> f(2, 3, 4)
4
```

Multiple assignments work in single statements:

```python
>>> area, circumference = pi * radius * radius, 2 * pi * radius
```

All right-side expressions evaluate before left-side names bind, enabling value swaps:

```python
>>> x, y = 3, 4.5
>>> y, x = x, y
```

## 1.2.5 Evaluating Nested Expressions

Evaluating call expressions follows this procedure:

1. Evaluate operator and operand subexpressions
2. Apply the function (operator value) to argument values

This recursive procedure applies itself repeatedly. For example:

```python
>>> sub(pow(2, add(1, 10)), pow(2, 5))
2016
```

An *expression tree* visualizes this hierarchical structure, with leaves representing functions or numbers and interior nodes showing call expressions.

Primitive expression evaluation rules:
- A numeral evaluates to the number it names
- A name evaluates to its associated value in the current environment

Environments provide essential context—expressions like `add(x, 1)` lack meaning without environment specifications for `x` and `add`.

## 1.2.6 The Non-Pure Print Function

Two function types exist:

**Pure functions** — return output through results, with no side effects:

```python
>>> abs(-2)
2
```

**Non-pure functions** — generate side effects beyond return values. The `print` function demonstrates this:

```python
>>> print(1, 2, 3)
1 2 3
```

Print always returns `None`:

```python
>>> two = print(2)
2
>>> print(two)
None
```

Nested print calls reveal non-pure behavior:

```python
>>> print(print(1), print(2))
1
2
None None
```

Pure functions offer advantages: reliable composition, simpler testing, and suitability for concurrent programming.


---

## Same Chapter

- [Ch1 1 Getting Started](ch1-1-getting-started.md)
- [Ch1 3 Defining New Functions](ch1-3-defining-new-functions.md)
- [Ch1 4 Designing Functions](ch1-4-designing-functions.md)
- [Ch1 5 Control](ch1-5-control.md)
- [Ch1 6 Higher Order Functions](ch1-6-higher-order-functions.md)
- [Ch1 7 Recursive Functions](ch1-7-recursive-functions.md)
