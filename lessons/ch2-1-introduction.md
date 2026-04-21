# 2.1 Introduction

Chapter 2 transitions from studying computational processes and functions to examining data representation and manipulation. "Effective use of built-in and user-defined data types are fundamental to data processing applications."

## 2.1.1 Native Data Types

Every Python value has a class that determines its type. Values sharing the same class exhibit consistent behavior. The `type()` function reveals an object's class:

```python
>>> type(2)
<class 'int'>
```

Native data types possess two key properties:

1. Expressions that evaluate to values of that type, called literals
2. Built-in functions and operators for manipulating those values

### Numeric Types

Python provides three native numeric types:
- **int**: Represents integers exactly without size limitations
- **float**: Represents real numbers using floating-point notation with finite precision
- **complex**: Represents complex numbers

### Float Considerations

Floats employ "floating point" representation, enabling representation of fractional values across a wide range. However, they introduce approximation limitations. "Float values should be treated as approximations to real values" since "not all numbers can be represented exactly."

Approximation errors emerge when combining floats:

```python
>>> 7 / 3 * 3
7.0

>>> 1 / 3 * 7 * 3
6.999999999999999
```

Division of integers produces float results.

### Non-Numeric Types

Beyond numbers, Python represents diverse data through native types like `bool` for True/False values. Most other data types require programmer-defined implementations.


---

## Same Chapter

- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
