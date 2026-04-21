# 2.3 Sequences

A sequence is an ordered collection of values representing a fundamental abstraction in computer science. "A sequence is an ordered collection of values" that shares common behaviors across different data types.

## Core Sequence Properties

Sequences must satisfy two essential conditions:

1. **Length**: "A sequence has a finite length. An empty sequence has length 0."
2. **Element selection**: "A sequence has an element corresponding to any non-negative integer index less than its length, starting at 0 for the first element."

## Lists

Lists are the primary native sequence type in Python. They support:

- **Creation and access**: `digits = [1, 8, 2, 8]` with index-based retrieval
- **Concatenation and repetition**: Lists can be combined with `+` and replicated with `*`
- **Nesting**: Lists can contain other lists for hierarchical structure

## Sequence Iteration

The `for` statement enables iteration over sequence elements without manual indexing:

```python
def count(s, value):
    total = 0
    for elem in s:
        if elem == value:
            total = total + 1
    return total
```

**Sequence unpacking** allows binding multiple names to sequence elements:

```python
for x, y in pairs:
    if x == y:
        same_count = same_count + 1
```

**Ranges** represent integer sequences created with `range()`, commonly used in for loops.

## Sequence Processing Patterns

### List Comprehensions

List comprehensions evaluate expressions for each element, optionally filtering:

```python
[x+1 for x in odds]
[x for x in odds if 25 % x == 0]
```

### Aggregation

Functions like `sum`, `min`, and `max` combine sequence values into single results.

### Higher-Order Functions

- `apply_to_all`: Apply a function to each element
- `keep_if`: Filter elements by condition
- `reduce`: Repeatedly apply a two-argument function

## Extended Sequence Behaviors

**Membership**: Test element presence with `in` and `not in` operators.

**Slicing**: Extract contiguous subsequences:

```python
digits[0:2]  # Elements at indices 0-1
digits[1:]   # Elements from index 1 onward
```

## Strings

Strings are sequences of characters supporting:

- Length and element selection
- Concatenation and repetition
- Substring membership testing with `in`
- Creation via `str()` constructor

## Trees

Trees impose hierarchical structure with a root label and branches. Implementation uses:

```python
def tree(root_label, branches=[]):
    return [root_label] + list(branches)

def label(tree):
    return tree[0]

def branches(tree):
    return tree[1:]
```

Tree-recursive functions process hierarchical data, exemplified by counting leaves and generating partition trees.

## Linked Lists

Linked lists represent sequences as nested pairs with the form `[first, rest]`:

```python
four = link(1, link(2, link(3, link(4, empty))))
```

Key operations include:

- `len_link`: Compute length iteratively
- `getitem_link`: Access elements by index
- Recursive variants for transformation
- `extend_link`, `apply_to_all_link`, `keep_if_link` for manipulation

Linked lists enable incremental sequence construction in recursive algorithms, particularly useful for partition enumeration and similar problems.


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
