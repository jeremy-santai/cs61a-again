# 2.4 Mutable Data

This section explores how data structures can change state over time, enabling modular program design through objects that manage their own internal state.

## The Object Metaphor

Objects combine data and behavior. "Objects combine data values with behavior. Objects represent information, but also behave like the things that they represent."

Objects have attributes (named values) and methods (function-valued attributes) accessed via dot notation. All values in Python are objects with behaviors matching their representations.

## Sequence Objects

Lists are **mutable**—their contents can change. Key mutation operations include:
- `pop()` - removes and returns final element
- `remove()` - removes first matching element
- `append()` - adds element to end
- `extend()` - adds all elements from another sequence
- `insert()` - inserts element at index
- Slice assignment - replaces portions of list

**Sharing and Identity:** Multiple names can reference the same list object. The `is` operator tests object identity (same object), while `==` tests value equality (same contents).

Tuples are **immutable** sequences created with comma-separated values, optionally in parentheses. While tuples cannot be modified, mutable elements within them can be changed.

## Dictionaries

Dictionaries store key-value pairs, providing lookup by descriptive keys rather than consecutive integers. Basic operations:

```python
numerals = {'I': 1, 'V': 5}
numerals['X'] = 10
numerals.get('A', 0)  # returns default if key absent
```

**Restrictions:** Dictionary keys cannot be mutable values, and each key maps to at most one value.

## Local State

Functions can maintain local state through **nonlocal assignment**. The `nonlocal` statement allows inner functions to modify bindings in parent frames:

```python
def make_withdraw(balance):
    def withdraw(amount):
        nonlocal balance
        if amount > balance:
            return 'Insufficient funds'
        balance = balance - amount
        return balance
    return withdraw
```

The nonlocal statement declares that assignment targets a name in an enclosing frame, not the local frame.

### Benefits and Costs

**Benefits:** Each instance maintains independent state inaccessible to the rest of the program, creating autonomous objects that model real-world entities evolving over time.

**Costs:** Non-local assignment violates **referential transparency**—expressions containing state-modifying operations cannot be freely substituted. This introduces complexity in reasoning about "sameness" between values that may share mutable structure.

## Advanced Implementation Patterns

### Message Passing

Data structures can be implemented as dispatch functions accepting message strings as arguments, with additional parameters for specific operations. This encapsulates all operations on a data type within one function.

### Dispatch Dictionaries

Rather than using conditionals for message dispatch, dictionaries map message strings to functions, enabling cleaner organization of behavior and state.

### Constraint-Based Systems

The constraint system demonstrates combining nonlocal assignment, lists, and dictionaries to build declarative programming abstractions. Constraints propagate values bidirectionally through connector networks, enabling computation in multiple directions from the same relationships.

Connectors hold values and participate in constraints through message passing. When a connector's value changes, it notifies associated constraints, which may update other connectors—creating automatic propagation through the network.


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
