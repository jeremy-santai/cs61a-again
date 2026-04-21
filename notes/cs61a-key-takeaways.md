# CS 61A: Key Takeaways

**Course Website:** [cs61a.org](../resources/course-website.md)

Based on:
- [Ants Project Summary](../resources/ants-project-summary.md) | [Code](../codebases/ants.py)
- [Cats Project Summary](../resources/cats-project-summary.md) | [Code](../codebases/cats.py)
- [Hog Project Summary](../resources/hog-project-summary.md) | [Code](../codebases/hog.py)
- [Scheme Interpreter Summary](../resources/scheme-interpreter-summary.md) | [Code](../codebases/scheme_classes.py)

---

## Chapter 1 — Building Blocks of Computation

**Lessons:** [1.1](../resources/lessons/ch1-1-getting-started.md) · [1.2](../resources/lessons/ch1-2-elements-of-programming.md) · [1.3](../resources/lessons/ch1-3-defining-new-functions.md) · [1.4](../resources/lessons/ch1-4-designing-functions.md) · [1.5](../resources/lessons/ch1-5-control.md) · [1.6](../resources/lessons/ch1-6-higher-order-functions.md) · [1.7](../resources/lessons/ch1-7-recursive-functions.md)

Every language has three mechanisms: **primitive expressions** (atoms), **means of combination** (call expressions, operators), and **means of abstraction** (naming, `def`). Mastering how Python evaluates nested call expressions — innermost first, left-to-right — is the foundation everything else builds on.

**Environment model.** Names are looked up in frames that chain to parent frames. Assignment creates a binding in the *current* frame; `nonlocal` lets inner functions rebind names in enclosing frames. This model explains closures, mutual recursion, and why two calls to the same function get independent local state.

**Functions as values.** A function is just a value that can be passed around, returned, or stored. Higher-order functions exploit this: `summation(n, term)` separates *what to accumulate* from *how to iterate*; `improve(update, close)` separates *how to update* from *when to stop*. The pattern shows up everywhere — strategy functions in Hog, predicate factories in Cats, decorator wrappers in exam problems.

**Closures.** When a nested function is returned, it carries its defining environment with it. This is how `make_adder(n)` remembers `n` after the outer call returns. Closures enable stateful functions without classes and are the mechanism behind `nonlocal`.

**Recursion.** The anatomy is always: base case + recursive case that moves toward it. Tree recursion (multiple calls per frame) is exponentially slower without memoization but naturally expresses problems like counting partitions, edit distance, or the Fibonacci sequence. The key skill is identifying what the function *promises* (its contract) and trusting that smaller recursive calls deliver on that promise.

**Design principles.** Single responsibility per function. DRY (name and reuse instead of copy-paste). Document with docstrings. Test with doctests — examples *are* the spec.

---

## Chapter 2 — Data

**Lessons:** [2.1](../resources/lessons/ch2-1-introduction.md) · [2.2](../resources/lessons/ch2-2-data-abstraction.md) · [2.3](../resources/lessons/ch2-3-sequences.md) · [2.4](../resources/lessons/ch2-4-mutable-data.md) · [2.5](../resources/lessons/ch2-5-object-oriented-programming.md) · [2.6](../resources/lessons/ch2-6-implementing-classes-and-objects.md) · [2.7](../resources/lessons/ch2-7-object-abstraction.md) · [2.8](../resources/lessons/ch2-8-efficiency.md) · [2.9](../resources/lessons/ch2-9-recursive-objects.md)

**Data abstraction.** Separate the *interface* (constructors and selectors) from the *representation*. Code that uses `numer(x)` and `denom(x)` doesn't care whether a rational number is stored as a list, tuple, or lambda. Violating this barrier ("abstraction violation") is always penalized — it couples code that should be independent.

**Sequences.** Lists, tuples, ranges, and strings all share the same interface: finite length, integer indexing. List comprehensions and `for` loops exploit this uniformity. Key distinction: lists are **mutable** (can be changed in place); tuples are **immutable** (safe to use as dict keys). The `is` operator tests identity (same object); `==` tests equality (same value).

**Mutation and shared state.** Mutation means the same object looks different to all names pointing at it. This enables data structures that *evolve*, but requires careful reasoning — especially when multiple references share a list. Dictionaries give O(1) lookup but keys must be immutable. `nonlocal` extends this to function-level state.

**Object-oriented programming.** Classes bundle state (instance attributes) with behavior (methods). The lookup chain is: instance `__dict__` → class `__dict__` → superclass `__dict__`. `__init__` runs once at construction; `self` is always the receiver object. Inheritance (`class B(A)`) lets B inherit and selectively override A's methods — the template method pattern (Ants) exploits this directly.

**Under the hood.** Classes and objects can be implemented with just functions and dictionaries (dispatch dictionaries). `bind_method` wraps a function so `self` is pre-filled. Understanding this demystifies dot notation and helps debug attribute errors.

**Special methods.** Python calls `__repr__`/`__str__` for display, `__len__`/`__getitem__` for sequence protocol, `__bool__` for truth testing, and `__call__` to make objects callable. Implementing these lets user-defined types integrate seamlessly with Python's syntax.

**Efficiency.** Count operations, not wall-clock time. Memoization (caching return values) converts exponential tree recursion to linear time. Θ-notation: Θ(1) constant, Θ(log n) logarithmic, Θ(n) linear, Θ(n²) quadratic, Θ(2ⁿ) exponential. Know which data structure operations are O(1) vs O(n): list indexing is O(1); list `in` is O(n); dict `in` is O(1).

**Recursive objects.** Linked lists and trees are defined recursively: a linked list is either empty or a first element plus a linked list. A tree is a root value plus a list of subtrees. Almost every tree problem decomposes as: handle the root, then recurse on each branch.

---

## Chapter 3 — Interpreters

**Lessons:** [3.1](../resources/lessons/ch3-1-introduction.md) · [3.2](../resources/lessons/ch3-2-functional-programming.md) · [3.3](../resources/lessons/ch3-3-exceptions.md) · [3.4](../resources/lessons/ch3-4-interpreters-combination.md) · [3.5](../resources/lessons/ch3-5-interpreters-abstraction.md)

**The big idea.** A program is text. An interpreter is a program that gives that text meaning. Writing an interpreter forces you to understand evaluation precisely — it's the deepest abstraction in the course.

**Eval-Apply cycle.** `scheme_eval` dispatches on expression type: symbols look up the environment, self-evaluating atoms return themselves, special forms are handled explicitly, call expressions evaluate the operator and operands then hand off to `scheme_apply`. `scheme_apply` creates a new frame whose parent is the function's defining environment (lexical scope), binds arguments, and evaluates the body.

**Scheme.** Pure functional subset: everything is an expression, no mutation, no statements. Special forms (`define`, `lambda`, `if`, `and`, `or`, `cond`, `let`, `begin`, `quote`) require special handling because they don't evaluate all sub-expressions normally. `define` binds a name; `lambda` creates a procedure; `quote` prevents evaluation.

**Tail calls.** A call in tail position doesn't need the current frame to finish — the callee's result *is* the caller's result. Proper tail-call optimization (TCO) recycles the frame instead of stacking a new one, enabling iteration-in-recursion-clothing without stack overflow.

**Exceptions.** `raise` signals a problem; `try/except` handles it. Exception classes form a hierarchy under `BaseException`. Catching a broad class (like `Exception`) catches all subclasses. Use specific exceptions for clean error handling; avoid silently catching everything.

**Pairs and nil.** The `Pair` class represents Scheme's cons cells. A Scheme list `(1 2 3)` is `Pair(1, Pair(2, Pair(3, nil)))`. `car`/`first` accesses the head; `cdr`/`rest` accesses the tail. Understanding this representation is essential for the interpreter project.

---

## Chapter 4 — Data Processing

**Lessons:** [4.1](../resources/lessons/ch4-1-introduction.md) · [4.2](../resources/lessons/ch4-2-implicit-sequences.md) · [4.3](../resources/lessons/ch4-3-declarative-programming.md) · [4.4](../resources/lessons/ch4-4-logic-programming.md) · [4.5](../resources/lessons/ch4-5-unification.md) · [4.6](../resources/lessons/ch4-6-distributed-computing.md) · [4.7](../resources/lessons/ch4-7-distributed-data-processing.md) · [4.8](../resources/lessons/ch4-8-parallel-computing.md)

**Lazy evaluation / iterators.** An iterator produces values on demand rather than materializing the whole sequence. `iter(x)` produces an iterator; `next(it)` advances it; `StopIteration` signals the end. Generators (`yield`) are syntactic sugar for writing iterators: execution suspends at each `yield` and resumes on the next `next()`. `yield from` delegates to a sub-iterator. Crucially, iterators are stateful and single-use — calling `iter()` on an iterator returns itself.

**Generator patterns.** `yield` from within a recursive call + `yield from` enables lazy tree traversal. Generators compose: pass one generator as input to another without materializing intermediate lists. This is the foundation of Python's `map`, `filter`, and `zip`.

**SQL / declarative programming.** Describe the *result* you want, not the steps to get it. Core syntax: `SELECT columns FROM table WHERE condition GROUP BY key HAVING agg-condition ORDER BY col LIMIT n`. Joins combine tables: `SELECT ... FROM t1, t2 WHERE t1.col = t2.col`. Aggregates (`SUM`, `COUNT`, `MAX`, `AVG`) collapse groups. The `HAVING` clause filters *after* grouping; `WHERE` filters *before*.

**Logic programming.** Facts declare relationships; queries find variable bindings that satisfy them. Compound facts add hypotheses (if-then rules). The interpreter searches systematically. Unification is the mechanism: it finds variable assignments making two expressions identical, handling variables on both sides simultaneously.

**Distributed systems.** Client/server splits responsibility — server provides a service, clients consume it. HTTP is the canonical protocol: GET requests, status codes (200 OK, 404 Not Found), headers then body. Peer-to-peer removes the central point of failure by making every node both client and server. MapReduce parallelizes large computations: map produces key-value pairs, shuffle groups by key, reduce aggregates each group.

**Parallelism.** Threads share memory; processes don't. Python's GIL limits CPU parallelism in threads — use multiprocessing for CPU-bound work. Shared mutable state under concurrency requires locks (`threading.Lock`) to prevent race conditions. Pure functional code (no mutation) is parallelism-safe by definition.

---

## Cross-Cutting Themes

| Theme | Where It Appears |
|-------|-----------------|
| **Abstraction barriers** | Data abstraction (ch2), OOP interfaces, SQL schema design |
| **Higher-order functions** | Ch1 HOFs, decorators, `map`/`filter`, SQL aggregates |
| **Recursive structure** | Linked lists, trees, Scheme lists, recursive descent parsing |
| **Environment / scope** | Ch1 closures, ch3 interpreter frames, Scheme `define`/`lambda` |
| **Lazy vs eager** | Generators (ch4), `range`, SQL (computed not stored) |
| **Declarative vs imperative** | SQL (ch4.3), logic programming (ch4.4) vs Python procedures |

---

## Exam Patterns

- **WWPD** — trace through the environment model step by step; watch for mutation vs rebinding, generator state, and `nonlocal`
- **Environment diagrams** — draw every frame; note parent pointers; mutation changes a box's value without creating a new binding
- **Code completion** — read the doctest first; let the examples pin down what the function must do before writing anything
- **Recursion** — identify the base case, what gets smaller, and what gets accumulated or returned; don't second-guess a correct recursive leap of faith
- **OOP** — trace attribute lookup: instance → class → superclass; `__init__` sets instance attributes; class attributes are shared
- **Scheme** — every expression has a value; `define` doesn't; special forms are not call expressions; check whether `nil`/empty-list cases are handled
- **SQL** — know the clause order (`SELECT … FROM … WHERE … GROUP BY … HAVING … ORDER BY … LIMIT`) and when each filter fires
