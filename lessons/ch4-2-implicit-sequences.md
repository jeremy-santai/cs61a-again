# 4.2 Implicit Sequences

A sequence can be represented without storing each element explicitly in memory. Instead, elements are computed on demand—a concept known as lazy computation. The range type exemplifies this: `range(10000, 1000000000)` doesn't store nearly a billion integers; it computes requested elements dynamically.

## 4.2.1 Iterators

An iterator provides sequential access to values through two mechanisms: retrieving the next element and signaling when the sequence ends.

Key functions:
- `iter()` — obtains an iterator from a container
- `next()` — retrieves the next element
- `StopIteration` — exception raised when no more values exist

Each iterator maintains position state. Multiple iterators over the same sequence track independent positions:

```python
r = range(3, 13)
s = iter(r)  # 1st iterator
next(s)      # Returns 3
t = iter(r)  # 2nd iterator
next(t)      # Returns 3
```

Calling `iter()` on an iterator returns that iterator itself, not a copy.

## 4.2.2 Iterables

An iterable value produces iterators when passed to `iter()`. Iterables include sequences (strings, tuples), containers (sets, dictionaries), and iterators themselves.

Dictionaries and sets maintain a defined iteration order, though programmers cannot control it. Structural changes (adding/removing keys) invalidate iterators, but modifying existing values does not.

## 4.2.3 Built-in Iterators

Functions like `map()`, `filter()`, `zip()`, and `reversed()` return iterators and support lazy evaluation. The `map()` function delays computation until elements are requested:

```python
doubled = map(double_and_print, range(3, 7))
next(doubled)  # Function called once
```

## 4.2.4 For Statements

The for loop operates on iterators by invoking `__iter__()` on the expression to obtain an iterator, then repeatedly calling `__next__()` until `StopIteration` is raised:

```python
for item in counts:
    print(item)
```

Equivalent to:

```python
items = counts.__iter__()
try:
    while True:
        item = items.__next__()
        print(item)
except StopIteration:
    pass
```

## 4.2.5 Generators and Yield Statements

A generator is an iterator returned by a generator function—one using `yield` instead of `return`. Generators simplify iterator implementation by avoiding manual state tracking:

```python
def letters_generator():
    current = 'a'
    while current <= 'd':
        yield current
        current = chr(ord(current)+1)
```

When `__next__()` is called, execution continues from the previous `yield` statement. Local variables persist across calls. The function raises `StopIteration` when it returns.

## 4.2.6 Iterable Interface

An iterable returns an iterator via `__iter__()`. Unlike iterators, iterables remain unchanged; each `__iter__()` call produces a fresh iterator:

```python
class Letters:
    def __init__(self, start='a', end='e'):
        self.start = start
        self.end = end
    def __iter__(self):
        return LetterIter(self.start, self.end)
```

This enables multiple independent iterations over the same data.

## 4.2.7 Creating Iterables with Yield

Generator functions can implement the iterable interface by returning new generators each time `__iter__()` is invoked:

```python
class LettersWithYield:
    def __init__(self, start='a', end='e'):
        self.start = start
        self.end = end
    def __iter__(self):
        next_letter = self.start
        while next_letter < self.end:
            yield next_letter
            next_letter = chr(ord(next_letter)+1)
```

This enables the sequence to be iterated multiple times.

## 4.2.8 Iterator Interface

The `__next__()` method returns the next element and advances the iterator's position. Iterators are mutable and exhaustible—once `StopIteration` is raised, it continues to be raised:

```python
class LetterIter:
    def __init__(self, start='a', end='e'):
        self.next_letter = start
        self.end = end
    def __next__(self):
        if self.next_letter == self.end:
            raise StopIteration
        letter = self.next_letter
        self.next_letter = chr(ord(letter)+1)
        return letter
```

Infinite sequences are possible by never raising `StopIteration`.

## 4.2.10 Python Streams

Streams are lazily computed linked lists. Unlike explicit linked lists, a stream computes its rest only when accessed via a property method:

```python
class Stream:
    class empty:
        def __repr__(self):
            return 'Stream.empty'
    empty = empty()
    
    def __init__(self, first, compute_rest=lambda: empty):
        self.first = first
        self._compute_rest = compute_rest
    
    @property
    def rest(self):
        if self._compute_rest is not None:
            self._rest = self._compute_rest()
            self._compute_rest = None
        return self._rest
```

### Infinite Streams

Streams represent infinite sequences:

```python
def integer_stream(first):
    def compute_rest():
        return integer_stream(first+1)
    return Stream(first, compute_rest)

positives = integer_stream(1)
```

### Stream Operations

`map_stream()` lazily applies functions:

```python
def map_stream(fn, s):
    if s is Stream.empty:
        return s
    def compute_rest():
        return map_stream(fn, s.rest)
    return Stream(fn(s.first), compute_rest)
```

`filter_stream()` lazily filters elements:

```python
def filter_stream(fn, s):
    if s is Stream.empty:
        return s
    def compute_rest():
        return filter_stream(fn, s.rest)
    if fn(s.first):
        return Stream(s.first, compute_rest)
    else:
        return compute_rest()
```

### Example: Sieve of Eratosthenes

```python
def primes(pos_stream):
    def not_divisible(x):
        return x % pos_stream.first != 0
    def compute_rest():
        return primes(filter_stream(not_divisible, pos_stream.rest))
    return Stream(pos_stream.first, compute_rest)

prime_numbers = primes(integer_stream(2))
```

### Advantages Over Iterators

Streams can be passed to pure functions multiple times without being "used up," unlike iterators. This makes them suitable for functional programming patterns.


---

## Same Chapter

- [Ch4 1 Introduction](ch4-1-introduction.md)
- [Ch4 3 Declarative Programming](ch4-3-declarative-programming.md)
- [Ch4 4 Logic Programming](ch4-4-logic-programming.md)
- [Ch4 5 Unification](ch4-5-unification.md)
- [Ch4 6 Distributed Computing](ch4-6-distributed-computing.md)
- [Ch4 7 Distributed Data Processing](ch4-7-distributed-data-processing.md)
- [Ch4 8 Parallel Computing](ch4-8-parallel-computing.md)
