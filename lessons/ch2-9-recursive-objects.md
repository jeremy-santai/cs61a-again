# 2.9 Recursive Objects

Objects can contain other objects as attributes. When an object contains an attribute of the same class type, it becomes a recursive object—a structure that refers to itself.

## 2.9.1 Linked List Class

A linked list consists of a first element and a remaining list. The remaining portion is itself a linked list, creating a recursive definition. The empty list serves as the base case.

### Implementation

The Link class uses special methods to integrate with Python's built-in functions:

```python
class Link:
    """A linked list with a first element and the rest."""
    empty = ()
    def __init__(self, first, rest=empty):
        assert rest is Link.empty or isinstance(rest, Link)
        self.first = first
        self.rest = rest
    def __getitem__(self, i):
        if i == 0:
            return self.first
        else:
            return self.rest[i-1]
    def __len__(self):
        return 1 + len(self.rest)
```

The `__len__` and `__getitem__` methods are recursive, with the base case occurring when `self.rest` equals `Link.empty`.

### String Representation

A helper function converts Link instances to readable strings:

```python
def link_expression(s):
    """Return a string that would evaluate to s."""
    if s.rest is Link.empty:
        rest = ''
    else:
        rest = ', ' + link_expression(s.rest)
    return 'Link({0}{1})'.format(s.first, rest)
```

Setting this as `__repr__` allows automatic string conversion.

### Higher-Order Functions

**map_link** applies a function to each element:

```python
def map_link(f, s):
    if s is Link.empty:
        return s
    else:
        return Link(f(s.first), map_link(f, s.rest))
```

**filter_link** retains elements satisfying a condition:

```python
def filter_link(f, s):
    if s is Link.empty:
        return s
    else:
        filtered = filter_link(f, s.rest)
        if f(s.first):
            return Link(s.first, filtered)
        else:
            return filtered
```

**join_link** concatenates elements with a separator:

```python
def join_link(s, separator):
    if s is Link.empty:
        return ""
    elif s.rest is Link.empty:
        return str(s.first)
    else:
        return str(s.first) + separator + join_link(s.rest, separator)
```

### Recursive Construction: Partitions

Linked lists excel at incrementally building sequences during recursive computation. The partitions function demonstrates this by enumerating integer partitions:

```python
def partitions(n, m):
    """Return a linked list of partitions of n using parts of up to m."""
    if n == 0:
        return Link(Link.empty)
    elif n < 0 or m == 0:
        return Link.empty
    else:
        using_m = partitions(n-m, m)
        with_m = map_link(lambda s: Link(m, s), using_m)
        without_m = partitions(n, m-1)
        return with_m + without_m
```

## 2.9.2 Tree Class

Trees are data structures where each node contains branches that are themselves trees.

### Implementation

```python
class Tree:
    def __init__(self, label, branches=()):
        self.label = label
        for branch in branches:
            assert isinstance(branch, Tree)
        self.branches = branches
    def __repr__(self):
        if self.branches:
            return 'Tree({0}, {1})'.format(self.label, repr(self.branches))
        else:
            return 'Tree({0})'.format(repr(self.label))
    def is_leaf(self):
        return not self.branches
```

Trees store values at internal nodes (labels) rather than only at leaves.

### Example: Fibonacci Tree

A tree can represent the computation history of recursive functions:

```python
def fib_tree(n):
    if n == 1:
        return Tree(0)
    elif n == 2:
        return Tree(1)
    else:
        left = fib_tree(n-2)
        right = fib_tree(n-1)
        return Tree(left.label + right.label, (left, right))
```

Recursive processing extracts values from trees:

```python
def sum_labels(t):
    """Sum the labels of a Tree instance, which may be None."""
    return t.label + sum([sum_labels(b) for b in t.branches])
```

### Memoization Benefits

Applying memoization dramatically reduces computation:

> "Instead of creating 18,454,929 different instances of the Tree class, we now create only 35."

Shared subtrees represent identical computations across the tree structure.

## 2.9.3 Sets

Python provides a built-in set type for unordered collections of distinct elements:

```python
s = {3, 2, 1, 4, 4}  # {1, 2, 3, 4}
3 in s  # True
s.union({1, 5})  # {1, 2, 3, 4, 5}
s.intersection({6, 5, 4, 3})  # {3, 4}
```

### Sets as Unordered Sequences

One representation uses linked lists without duplicates:

```python
def set_contains(s, v):
    """Return True if and only if set s contains v."""
    if empty(s):
        return False
    elif s.first == v:
        return True
    else:
        return set_contains(s.rest, v)
```

This approach requires Θ(n) time for membership tests.

### Sets as Ordered Sequences

Ordering elements enables early termination in searches, reducing intersection complexity from Θ(n²) to Θ(n):

```python
def intersect_set(set1, set2):
    if empty(set1) or empty(set2):
        return Link.empty
    else:
        e1, e2 = set1.first, set2.first
        if e1 == e2:
            return Link(e1, intersect_set(set1.rest, set2.rest))
        elif e1 < e2:
            return intersect_set(set1.rest, set2)
        elif e2 < e1:
            return intersect_set(set1, set2.rest)
```

### Sets as Binary Search Trees

A more efficient representation organizes elements in a balanced binary tree, enabling Θ(log n) search time:

```python
def set_contains(s, v):
    if s is None:
        return False
    elif s.entry == v:
        return True
    elif s.entry < v:
        return set_contains(s.right, v)
    elif s.entry > v:
        return set_contains(s.left, v)
```

### Python's Built-in Implementation

Python's set type uses hashing for constant-time operations. Built-in sets cannot contain mutable types, though the immutable `frozenset` class provides nested set support.


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
