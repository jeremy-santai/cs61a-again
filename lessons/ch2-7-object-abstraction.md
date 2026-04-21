# 2.7 Object Abstraction

This section explores how Python's object system enables abstract data representations and supports multiple data representations simultaneously through generic functions.

## 2.7.1 String Conversion

Python requires objects to produce two string representations:

- **str()**: Returns human-readable text
- **repr()**: Returns a Python-interpretable expression where possible

The underlying mechanism uses special methods: `__repr__()` and `__str__()`. When you call `repr(obj)`, Python invokes `obj.__repr__()`. This allows user-defined classes to extend these functions to new types.

Example distinction between the two approaches:
```python
from datetime import date
tues = date(2011, 9, 12)
repr(tues)      # 'datetime.date(2011, 9, 12)'
str(tues)       # '2011-09-12'
```

## 2.7.2 Special Methods

Python defines special method names that the interpreter invokes automatically in specific contexts:

**Truth Values (`__bool__`)**: Controls whether an object is truthy or falsy:
```python
Account.__bool__ = lambda self: self.balance != 0
```

**Sequence Operations**:
- `__len__()`: Invoked by `len()` function
- `__getitem__()`: Invoked by element selection operator `[]`

**Callable Objects (`__call__`)**: Makes objects behave like functions:
```python
class Adder(object):
    def __init__(self, n):
        self.n = n
    def __call__(self, k):
        return self.n + k
```

**Arithmetic Operations**: Methods like `__add__()` and `__radd__()` enable operator overloading.

## 2.7.3 Multiple Representations

Complex numbers illustrate supporting multiple representations within one program. They can be represented as:
- **Rectangular form**: real and imaginary parts
- **Polar form**: magnitude and angle

### Interfaces

An interface is "a set of shared attribute names, along with a specification of their behavior." Complex number arithmetic requires four attributes: `real`, `imag`, `magnitude`, and `angle`.

### Properties

The `@property` decorator computes attributes dynamically from methods, maintaining consistency between representations without storing redundant data:

```python
from math import atan2
class ComplexRI(Complex):
    def __init__(self, real, imag):
        self.real = real
        self.imag = imag
    @property
    def magnitude(self):
        return (self.real ** 2 + self.imag ** 2) ** 0.5
    @property
    def angle(self):
        return atan2(self.imag, self.real)
```

The interface approach is **additive**: new representations can be added without modifying existing code, provided they implement the required attributes.

## 2.7.4 Generic Functions

Generic functions apply to arguments of different types. Three implementation approaches exist:

### Type Dispatching

Inspect argument types and execute appropriate code branches:

```python
class Number:
    def __add__(self, other):
        if self.type_tag == other.type_tag:
            return self.add(other)
        elif (self.type_tag, other.type_tag) in self.adders:
            return self.cross_apply(other, self.adders)
    
    adders = {("com", "rat"): add_complex_and_rational,
              ("rat", "com"): add_rational_and_complex}
```

This dictionary-based approach allows new types to register cross-type operations.

### Coercion

Transform objects to a common type before performing operations:

```python
def rational_to_complex(r):
    return ComplexRI(r.numer/r.denom, 0)

class Number:
    def __add__(self, other):
        x, y = self.coerce(other)
        return x.add(y)
    
    coercions = {('rat', 'com'): rational_to_complex}
```

**Advantages**: Fewer functions needed (one per type pair, not per operation)

**Disadvantages**: Can lose information during conversion; exact rationals become approximate when converted to complex numbers.


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
