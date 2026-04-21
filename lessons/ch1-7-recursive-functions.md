# 1.7 Recursive Functions

A function becomes recursive when its body calls itself, either directly or indirectly. "A function is called *recursive* if the body of the function calls the function itself, either directly or indirectly."

## 1.7.1 The Anatomy of Recursive Functions

The foundational example uses digit summation. For the number 18117, the algorithm separates the last digit (7) from the remaining digits (1811), then recursively sums the remaining digits before adding the final digit:

```python
def sum_digits(n):
    """Return the sum of the digits of positive integer n."""
    if n < 10:
        return n
    else:
        all_but_last, last = n // 10, n % 10
        return sum_digits(all_but_last) + last
```

Recursive functions follow a consistent structure:

1. **Base Case**: A conditional statement handling the simplest inputs (e.g., single-digit numbers)
2. **Recursive Calls**: Calls that simplify the original problem by working with smaller inputs

Recursive functions "simplify problems incrementally," with each subsequent call requiring less computational work.

### Factorial Comparison

The text contrasts two approaches:

**Iterative approach** accumulates results from base case upward using explicit state management:
```python
def fact_iter(n):
    total, k = 1, 1
    while k <= n:
        total, k = total * k, k + 1
    return total
```

**Recursive approach** expresses the solution directly through self-reference:
```python
def fact(n):
    if n == 1:
        return 1
    else:
        return n * fact(n-1)
```

## 1.7.2 Mutual Recursion

Functions can call each other in alternating sequence. The example demonstrates determining even/odd:

```python
def is_even(n):
    if n == 0:
        return True
    else:
        return is_odd(n-1)

def is_odd(n):
    if n == 0:
        return False
    else:
        return is_even(n-1)
```

## 1.7.3 Printing in Recursive Functions

Recursive implementations often involve printing intermediate results. The key insight is that recursive calls create a chain of deferred operations, printed from the innermost call outward.

## 1.7.4 Tree Recursion

When a function makes multiple recursive calls, it creates branching computation patterns. Fibonacci exemplifies this:

```python
def fib(n):
    if n == 1:
        return 0
    if n == 2:
        return 1
    else:
        return fib(n-2) + fib(n-1)
```

## 1.7.5 Example: Partitions

A practical tree recursion problem counts integer partitions. The `count_partitions(n, m)` function determines how many ways to express n as a sum of integers up to m:

```python
def count_partitions(n, m):
    """Count the ways to partition n using parts up to m."""
    if n == 0:
        return 1
    elif n < 0:
        return 0
    elif m == 0:
        return 0
    else:
        return count_partitions(n-m, m) + count_partitions(n, m-1)
```

## Key Insights

The "recursive leap of faith"—trusting that recursive calls correctly solve simpler subproblems without manually tracing their execution. This approach mirrors mathematical proof by induction.

Recursive solutions often require fewer explicit state variables than iterative counterparts, with computation state maintained implicitly through the call stack and environment frames.


---

## Same Chapter

- [Ch1 1 Getting Started](ch1-1-getting-started.md)
- [Ch1 2 Elements Of Programming](ch1-2-elements-of-programming.md)
- [Ch1 3 Defining New Functions](ch1-3-defining-new-functions.md)
- [Ch1 4 Designing Functions](ch1-4-designing-functions.md)
- [Ch1 5 Control](ch1-5-control.md)
- [Ch1 6 Higher Order Functions](ch1-6-higher-order-functions.md)
