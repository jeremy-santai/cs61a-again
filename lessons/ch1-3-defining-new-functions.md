# 1.3 Defining New Functions

Function definitions allow users to bind names to compound operations, creating reusable units of code.

## Basic Function Definition

The simplest example demonstrates squaring a number:

```python
def square(x):
    return mul(x, x)
```

Function definitions follow this structure:

```python
def <name>(<formal parameters>):
    return <return expression>
```

The second line must be indented (typically four spaces). The return expression is stored as part of the function and evaluated only when called.

Once defined, functions work like built-in functions:

```python
square(21)          # Returns 441
square(add(2, 5))   # Returns 49
square(square(3))   # Returns 81
```

Functions serve as building blocks for other functions:

```python
def sum_squares(x, y):
    return add(square(x), square(y))

sum_squares(3, 4)   # Returns 25
```

## 1.3.1 Environments

An environment consists of a sequence of frames containing name-to-value bindings. The global frame holds shared bindings; assignment and import statements add entries here.

**Environment diagrams** visualize these bindings and their values. Functions appear in diagrams showing their names and formal parameters.

### Bound Names vs. Intrinsic Names

A function has two names: the **bound name** in a frame and the **intrinsic name** within the function itself. The bound name is used during evaluation; the intrinsic name plays no evaluative role.

## 1.3.2 Calling User-Defined Functions

To apply a user-defined function:

1. Bind arguments to formal parameter names in a new local frame
2. Execute the function body using an environment starting with this local frame

Each function call creates its own independent local frame.

## 1.3.3 Example: Calling a User-Defined Function

The example traces `sum_squares(5, 12)`:

```python
from operator import add, mul
def square(x):
    return mul(x, x)
def sum_squares(x, y):
    return add(square(x), square(y))
result = sum_squares(5, 12)
```

This creates nested local frames for each function call, ultimately returning 169.

**Name Evaluation:** "A name evaluates to the value bound to that name in the earliest frame of the current environment in which that name is found."

## 1.3.4 Local Names

Parameter names are local to their function bodies. Different functions can use the same parameter names without confusion due to independent local frames.

**Scope** refers to the region where a name remains accessible. Local names are scoped to their function's body.

## 1.3.5 Choosing Names

Python style guidelines recommend:

- Function names: lowercase with underscores separating words
- Names should evoke operations or resulting quantities
- Parameter names: lowercase, single words preferred
- Single-letter parameters acceptable when roles are obvious
- Avoid ambiguous characters like lowercase "l" or capital "O"

## 1.3.6 Functions as Abstractions

A key property of functions is abstraction—users need not understand implementation details. Functions should suppress unnecessary complexity.

**Three core attributes of functional abstractions:**

- **Domain:** set of acceptable arguments
- **Range:** set of possible return values
- **Intent:** the relationship computed between inputs and outputs

## 1.3.7 Operators

Infix operators like `+` and `-` are shorthand for function calls:

```python
2 + 3      # Equivalent to add(2, 3)
2 + 3 * 4 + 5   # Follows standard mathematical precedence
```

Parentheses override precedence:

```python
(2 + 3) * (4 + 5)   # Equivalent to mul(add(2, 3), add(4, 5))
```

**Division operators:**

- `/` produces floating-point results: `5 / 4` returns `1.25`
- `//` rounds down to integers: `5 // 4` returns `1`

These correspond to `truediv` and `floordiv` functions.


---

## Same Chapter

- [Ch1 1 Getting Started](ch1-1-getting-started.md)
- [Ch1 2 Elements Of Programming](ch1-2-elements-of-programming.md)
- [Ch1 4 Designing Functions](ch1-4-designing-functions.md)
- [Ch1 5 Control](ch1-5-control.md)
- [Ch1 6 Higher Order Functions](ch1-6-higher-order-functions.md)
- [Ch1 7 Recursive Functions](ch1-7-recursive-functions.md)
