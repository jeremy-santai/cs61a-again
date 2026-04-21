# CS 61A — Practice Final Exam

**Time allowed:** 3 hours
**Total points:** 75
**Instructions:** Write your answers clearly. For coding questions, your code must match the given doctests. If a Python expression would cause an error, write `ERROR`. If a function would run forever, write `INFINITE LOOP`.

---

## Problem 1 — What Would Python Display? (8 points)

Assume the following code has been executed:

```python
def bounce(n):
    if n == 0:
        yield 0
    else:
        yield n
        yield from bounce(n - 1)
        yield n

def window(s, k):
    result = []
    for x in s:
        result.append(x)
        if len(result) == k:
            yield list(result)
            result.pop(0)

pairs = [[i, i * 2] for i in range(1, 4)]
```

For each expression, write exactly what Python would print when passed to `print(...)`. Write `ERROR` if an exception is raised.

**(a) (2 pts)**
```python
print(list(bounce(2)))
```

**(b) (2 pts)**
```python
t = bounce(3)
next(t)
next(t)
print(next(t))
```

**(c) (2 pts)**
```python
print(list(window([1, 2, 3, 4, 5], 3)))
```

**(d) (2 pts)**
```python
print([x for row in pairs for x in row if x > 3])
```

---

## Problem 2 — Environment Diagrams (6 points)

Draw the environment diagram for the following code, then answer the questions. **Only the answers are graded.**

```python
def make(x):
    def f(y):
        nonlocal x
        x = x + y
        return x
    return f

a = make(3)
b = make(10)
print(a(2))   # line A
print(b(1))   # line B
print(a(4))   # line C
```

**(a) (2 pts)** What is printed on **line A**?

**(b) (2 pts)** What is printed on **line B**?

**(c) (2 pts)** What is printed on **line C**?

---

## Problem 3 — List Manipulation (6 points)

Implement `flatten`, which takes a (possibly nested) list and returns a flat list of all the non-list elements, in order.

```python
def flatten(s):
    """Return a flat list containing all non-list elements of s.

    >>> flatten([1, [2, 3], [4, [5, 6]], 7])
    [1, 2, 3, 4, 5, 6, 7]
    >>> flatten([[[1]], [2, [3, [4]]]])
    [1, 2, 3, 4]
    >>> flatten([])
    []
    """
    result = []
    for x in s:
        ______(a)______
    return result
```

**(a) (6 pts)** Fill in the body of the `for` loop (you may use multiple lines).

---

## Problem 4 — Higher-Order Functions (10 points)

**(a) (5 pts)** Implement `compose_all`, which takes a list of single-argument functions and returns a new function that applies them all in order (left to right).

```python
def compose_all(fns):
    """Return a function that applies every function in fns left to right.

    >>> double = lambda x: x * 2
    >>> add1 = lambda x: x + 1
    >>> f = compose_all([double, add1, double])
    >>> f(3)   # double(3)=6, add1(6)=7, double(7)=14
    14
    >>> compose_all([])(99)
    99
    """
```

**(b) (5 pts)** Implement `count_calls`, a decorator that wraps a function so that every call increments a shared counter. The returned function should also have a `.count` attribute containing the total number of times it has been called.

```python
def count_calls(fn):
    """Return a wrapped version of fn that tracks how many times it has been called.

    >>> @count_calls
    ... def square(x):
    ...     return x * x
    >>> square(3)
    9
    >>> square(5)
    25
    >>> square.count
    2
    """
```

---

## Problem 5 — Recursion (10 points)

**(a) (5 pts)** Implement `paths`, which takes a 2-D list `grid` (list of rows) and returns the number of paths from the top-left corner to the bottom-right corner. You may only move **right** or **down** one cell at a time. A cell with value `0` is blocked and cannot be entered.

```python
def paths(grid):
    """Return the number of paths from grid[0][0] to grid[-1][-1] moving only right or down.
    Cells with value 0 are impassable.

    >>> paths([[1, 1], [1, 1]])
    2
    >>> paths([[1, 1, 1], [1, 0, 1], [1, 1, 1]])
    2
    >>> paths([[1, 0], [1, 1]])
    1
    >>> paths([[0, 1], [1, 1]])
    0
    """
```

**(b) (5 pts)** Implement `has_sum`, which takes a list of positive integers `s` and a target `n`. It returns `True` if any **subset** of elements in `s` sums to exactly `n`, and `False` otherwise.

```python
def has_sum(s, n):
    """Return True if any subset of s sums to n.

    >>> has_sum([3, 1, 4, 1, 5], 9)   # 4 + 5
    True
    >>> has_sum([3, 1, 4, 1, 5], 6)   # 1 + 1 + 4  or  1 + 5
    True
    >>> has_sum([3, 1, 4, 1, 5], 2)
    False
    >>> has_sum([], 0)
    True
    """
```

---

## Problem 6 — Object-Oriented Programming (12 points)

A `Library` holds `Book` instances. Implement the classes below.

- `Book` has a `title` (string) and `copies` (integer, the number available).
- `Book.checkout()` reduces `copies` by 1 and returns `True`. If no copies are available it prints `"No copies of <title> available"` and returns `False`.
- `Book.return_book()` increases `copies` by 1.
- `Library` has a list `collection` of `Book` instances (starts empty).
- `Library.add(book)` adds a `Book` to the collection.
- `Library.checkout(title)` finds the book with the matching title and calls its `checkout` method. If no book with that title exists, print `"Title not found"`.
- `Library.available()` returns a list of titles (strings) for every book that has at least one copy available, in the order they were added.

```python
class Book:
    """A book with a title and a number of available copies.

    >>> b = Book('Dune', 3)
    >>> b.checkout()
    True
    >>> b.copies
    2
    >>> b.return_book()
    >>> b.copies
    3
    """

class Library:
    """A collection of books.

    >>> lib = Library()
    >>> lib.add(Book('Dune', 2))
    >>> lib.add(Book('Foundation', 0))
    >>> lib.add(Book('Neuromancer', 1))
    >>> lib.available()
    ['Dune', 'Neuromancer']
    >>> lib.checkout('Foundation')
    No copies of Foundation available
    >>> lib.checkout('Dune')
    >>> lib.available()
    ['Dune', 'Neuromancer']
    >>> lib.checkout('Dune')
    >>> lib.available()
    ['Neuromancer']
    >>> lib.checkout('Hyperion')
    Title not found
    """
```

---

## Problem 7 — Trees (10 points)

Use the standard `Tree` class:

```python
class Tree:
    def __init__(self, label, branches=[]):
        self.label = label
        self.branches = list(branches)
    def is_leaf(self):
        return not self.branches
```

**(a) (5 pts)** Implement `prune_small`, which takes a tree `t` and a positive integer `n`. It returns a new tree where any node with **more than `n` branches** keeps only the `n` branches with the **largest labels** (ties broken arbitrarily). Nodes with `n` or fewer branches are unchanged. The pruning is applied at every level of the tree.

```python
def prune_small(t, n):
    """Return a copy of t keeping at most n branches per node (largest labels).

    >>> t = Tree(1, [Tree(5), Tree(3), Tree(8), Tree(2)])
    >>> prune_small(t, 2).branches[0].label   # keeps 8 and 5
    8
    >>> len(prune_small(t, 2).branches)
    2
    >>> prune_small(Tree(1, [Tree(2)]), 3).branches[0].label
    2
    """
```

**(b) (5 pts)** Implement `level_sum`, which takes a tree `t` and returns a list where `result[k]` is the sum of all labels at depth `k` (root is depth 0).

```python
def level_sum(t):
    """Return a list of label sums at each depth.

    >>> t = Tree(1, [Tree(2, [Tree(4), Tree(5)]), Tree(3, [Tree(6)])])
    >>> level_sum(t)
    [1, 5, 15]
    >>> level_sum(Tree(7))
    [7]
    """
```

---

## Problem 8 — Scheme (8 points)

**(a) (4 pts)** Implement `deep-map`, a Scheme procedure that takes a procedure `f` and a (possibly nested) list `s`, and returns a new list structure where `f` is applied to every non-pair element.

```scheme
;;; Apply f to every atom in s, preserving structure.
;;;
;;; scm> (deep-map (lambda (x) (* x x)) '(1 (2 3) (4 (5))))
;;; (1 (4 9) (16 (25)))
;;; scm> (deep-map - '())
;;; ()

(define (deep-map f s)
  _______)
```

**(b) (4 pts)** Implement `count-if`, a tail-recursive Scheme procedure that counts how many elements in a flat list satisfy a predicate `pred`.

```scheme
;;; Count elements in s satisfying pred. Must be tail-recursive.
;;;
;;; scm> (count-if odd? '(1 2 3 4 5))
;;; 3
;;; scm> (count-if (lambda (x) (> x 3)) '(1 2 3 4 5))
;;; 2
;;; scm> (count-if number? '())
;;; 0

(define (count-if pred s)
  _______)
```

---

## Problem 9 — SQL (5 points)

The following two tables are defined:

```sql
CREATE TABLE students (name TEXT, grade INTEGER, club TEXT);
CREATE TABLE clubs (club TEXT, advisor TEXT, room INTEGER);
```

**(a) (2 pts)** Write a query that returns the `name` and `advisor` of every student, matched to their club's advisor. Only include students who have a matching club in the `clubs` table.

```sql
SELECT _______ FROM _______ ;
```

**(b) (3 pts)** Write a query that returns each `club` name and the **average grade** of its members, but only for clubs where the average grade is **above 10**. Label the average column `avg_grade`.

```sql
SELECT _______ FROM _______ ;
```

---

## Answers

<details>
<summary>Click to reveal solutions</summary>

### Problem 1

**(a)** `[2, 1, 0, 1, 2]`

**(b)** `2`
_(t yields 3, 2, 1 — third call returns 1? No: bounce(3) yields 3, then yield from bounce(2): yields 2, then yield from bounce(1): yields 1, yield from bounce(0): yields 0, then yields 1, then yields 2, then yields 3. So: next→3, next→2, next→1. Prints `1`.)_

**(c)** `[[1, 2, 3], [2, 3, 4], [3, 4, 5]]`

**(d)** `[4, 6]`
_(pairs = [[1,2],[2,4],[3,6]]; flattened with filter x>3 → 4, 6)_

---

### Problem 2

**(a)** `5` _(3+2)_

**(b)** `11` _(10+1)_

**(c)** `9` _(5+4, because x was updated to 5 in call (a))_

---

### Problem 3

```python
if isinstance(x, list):
    result.extend(flatten(x))
else:
    result.append(x)
```

---

### Problem 4

**(a)**
```python
def compose_all(fns):
    def composed(x):
        for f in fns:
            x = f(x)
        return x
    return composed
```

**(b)**
```python
def count_calls(fn):
    def wrapper(*args, **kwargs):
        wrapper.count += 1
        return fn(*args, **kwargs)
    wrapper.count = 0
    return wrapper
```

---

### Problem 5

**(a)**
```python
def paths(grid):
    rows, cols = len(grid), len(grid[0])
    def helper(r, c):
        if r >= rows or c >= cols or grid[r][c] == 0:
            return 0
        if r == rows - 1 and c == cols - 1:
            return 1
        return helper(r + 1, c) + helper(r, c + 1)
    return helper(0, 0)
```

**(b)**
```python
def has_sum(s, n):
    if n == 0:
        return True
    if not s:
        return False
    return has_sum(s[1:], n - s[0]) or has_sum(s[1:], n)
```

---

### Problem 6

```python
class Book:
    def __init__(self, title, copies):
        self.title = title
        self.copies = copies

    def checkout(self):
        if self.copies == 0:
            print(f'No copies of {self.title} available')
            return False
        self.copies -= 1
        return True

    def return_book(self):
        self.copies += 1

class Library:
    def __init__(self):
        self.collection = []

    def add(self, book):
        self.collection.append(book)

    def checkout(self, title):
        for book in self.collection:
            if book.title == title:
                book.checkout()
                return
        print('Title not found')

    def available(self):
        return [book.title for book in self.collection if book.copies > 0]
```

---

### Problem 7

**(a)**
```python
def prune_small(t, n):
    pruned = sorted(t.branches, key=lambda b: b.label, reverse=True)[:n]
    return Tree(t.label, [prune_small(b, n) for b in pruned])
```

**(b)**
```python
def level_sum(t):
    result = []
    level = [t]
    while level:
        result.append(sum(node.label for node in level))
        level = [b for node in level for b in node.branches]
    return result
```

---

### Problem 8

**(a)**
```scheme
(define (deep-map f s)
  (cond ((null? s) '())
        ((pair? (car s)) (cons (deep-map f (car s)) (deep-map f (cdr s))))
        (else (cons (f (car s)) (deep-map f (cdr s))))))
```

**(b)**
```scheme
(define (count-if pred s)
  (define (helper lst acc)
    (cond ((null? lst) acc)
          ((pred (car lst)) (helper (cdr lst) (+ acc 1)))
          (else (helper (cdr lst) acc))))
  (helper s 0))
```

---

### Problem 9

**(a)**
```sql
SELECT students.name, clubs.advisor
FROM students JOIN clubs ON students.club = clubs.club;
```

**(b)**
```sql
SELECT club, AVG(grade) AS avg_grade
FROM students
GROUP BY club
HAVING avg_grade > 10;
```

</details>
