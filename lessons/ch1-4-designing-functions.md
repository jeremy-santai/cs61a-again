# 1.4 Designing Functions

Functions serve as the primary medium to express computational processes in programming. Good function design reinforces the concept that functions are abstractions.

## Key Principles

**Single Responsibility**: "Each function should have exactly one job. That job should be identifiable with a short name and characterizable in a single line of text."

**DRY Principle**: The DRY (Don't Repeat Yourself) principle states that redundant code should be implemented once, named, and reused rather than duplicated throughout a program.

**General Design**: Functions should be defined generally rather than for specific cases. For example, Python includes a general `pow` function rather than a specialized squaring function.

These guidelines enhance code readability, reduce errors, and minimize overall code volume.

## 1.4.1 Documentation

Functions should include docstrings—documentation strings that describe the function's purpose. "The first line describes the job of the function in one line. The following lines can describe arguments and clarify the behavior of the function."

Example:
```python
def pressure(v, t, n):
    """Compute the pressure in pascals of an ideal gas.

    Applies the ideal gas law: http://en.wikipedia.org/wiki/Ideal_gas_law

    v -- volume of gas, in cubic meters
    t -- absolute temperature in degrees kelvin
    n -- particles of gas
    """
    k = 1.38e-23  # Boltzmann's constant
    return n * k * t / v
```

Comments using `#` can explain specific code lines but don't appear in help documentation.

## 1.4.2 Default Argument Values

Functions with many arguments can be difficult to use. Python supports default argument values, making optional parameters easier to manage:

```python
def pressure(v, t, n=6.022e23):
    """Compute the pressure in pascals of an ideal gas.

    v -- volume of gas, in cubic meters
    t -- absolute temperature in degrees kelvin
    n -- particles of gas (default: one mole)
    """
    k = 1.38e-23  # Boltzmann's constant
    return n * k * t / v
```

Usage:
```python
>>> pressure(1, 273.15)
2269.974834
>>> pressure(1, 273.15, 3 * 6.022e23)
6809.924502
```

In the function definition, `=` indicates a default value. When calling the function, arguments with defaults may be omitted.


---

## Same Chapter

- [Ch1 1 Getting Started](ch1-1-getting-started.md)
- [Ch1 2 Elements Of Programming](ch1-2-elements-of-programming.md)
- [Ch1 3 Defining New Functions](ch1-3-defining-new-functions.md)
- [Ch1 5 Control](ch1-5-control.md)
- [Ch1 6 Higher Order Functions](ch1-6-higher-order-functions.md)
- [Ch1 7 Recursive Functions](ch1-7-recursive-functions.md)
