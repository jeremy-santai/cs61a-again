# 2.8 Efficiency

Decisions about data representation and processing are often guided by efficiency considerations, referring to computational resources like time and memory required for computation.

## 2.8.1 Measuring Efficiency

Rather than measuring exact execution time, a more reliable approach involves counting specific events, such as function calls. The section illustrates this with the Fibonacci function:

```python
def fib(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fib(n-2) + fib(n-1)
```

Tree-recursive functions like this involve substantial redundant computation. A counting mechanism demonstrates the inefficiency: computing `fib(19)` requires 13,529 calls despite returning only 4,181.

**Space considerations** involve tracking active environments during evaluation. The space requirement for tree-recursive functions is proportional to maximum tree depth. Computing `fib(19)` requires at most 19 active frames while needing thousands of total calls.

## 2.8.2 Memoization

Memoization improves recursive function efficiency by storing previously computed results:

```python
def memo(f):
    cache = {}
    def memoized(n):
        if n not in cache:
            cache[n] = f(n)
        return cache[n]
    return memoized
```

This technique transforms tree-recursive processes into linear ones. With memoization, computing `fib(34)` requires only 35 function calls instead of millions.

## 2.8.3 Orders of Growth

Order of growth characterizes how resource requirements scale with input size. Using theta notation, R(n) = Θ(f(n)) means positive constants k₁ and k₂ exist such that k₁·f(n) ≤ R(n) ≤ k₂·f(n) for sufficiently large n.

The `count_factors` function demonstrates Θ(√n) growth by iterating up to the square root of its input.

## 2.8.4 Example: Exponentiation

Three approaches to computing bⁿ show different efficiencies:

**Linear recursion:**
```python
def exp(b, n):
    if n == 0:
        return 1
    return b * exp(b, n-1)
```
Requires Θ(n) steps and space.

**Successive squaring:**
```python
def fast_exp(b, n):
    if n == 0:
        return 1
    if n % 2 == 0:
        return square(fast_exp(b, n//2))
    else:
        return b * fast_exp(b, n-1)
```
Achieves Θ(log n) growth, computing b¹⁰⁰⁰ in approximately 14 multiplications versus 1,000.

## 2.8.5 Growth Categories

Common growth categories from slowest to fastest:

| Category | Notation | Example |
|----------|----------|---------|
| Constant | Θ(1) | abs |
| Logarithmic | Θ(log n) | fast_exp |
| Linear | Θ(n) | exp |
| Quadratic | Θ(n²) | nested loops |
| Exponential | Θ(bⁿ) | tree-recursive fib |

Key principles: constant multipliers are ignored, logarithm bases don't affect order, nested processes multiply orders, and lower-order terms are dropped from sums.

The tree-recursive Fibonacci computation requires Θ(φⁿ) steps, where φ ≈ 1.618 is the golden ratio, illustrating how exponential growth becomes impractical for large inputs.


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
