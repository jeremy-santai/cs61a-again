# 4.5 Unification

The query interpreter performs inference through **unification**, a method for matching queries to facts that may contain variables. The interpreter searches through related facts to find variable assignments that satisfy queries.

## 4.5.1 Pattern Matching

A pattern matches an expression when variable bindings exist such that substituting values into the pattern produces the expression. For example, the query `(query (parent abraham ?child))` and fact `(fact (parent abraham barack))` match when `?child` binds to `barack`.

The expression `((a b) c (a b))` matches pattern `(?x c ?x)` with `?x` bound to `(a b)`, and also matches `((a ?y) ?z (a b))` with `?y` bound to `b` and `?z` bound to `c`.

## 4.5.2 Representing Facts and Queries

Both queries and facts use Scheme lists with Pair classes and nil objects. The `unify` function takes two inputs plus an environment tracking variable bindings.

Example demonstration:
```python
>>> e = read_line("((a b) c (a b))")
>>> f = read_line("(?x c ?x)")
>>> env = Frame(None)
>>> unify(e, f, env)
True
>>> env.bindings
{'?x': Pair('a', Pair('b', nil))}
```

## 4.5.3 The Unification Algorithm

Unification generalizes pattern matching to handle expressions with variables on both sides. The recursive process continues until contradictions arise or viable bindings establish.

The unification algorithm follows these steps:

1. Replace inputs with their values if they are variables
2. Return success if inputs are equal
3. Bind variable to other expression if one is a variable
4. Return failure if neither is variable, both aren't lists, and differ
5. If both are pairs, recursively unify corresponding elements

```python
def unify(e, f, env):
    """Destructively extend ENV so as to unify (make equal) e and f, returning
    True if this succeeds and False otherwise."""
    e = lookup(e, env)
    f = lookup(f, env)
    if e == f:
        return True
    elif isvar(e):
        env.define(e, f)
        return True
    elif isvar(f):
        env.define(f, e)
        return True
    elif scheme_atomp(e) or scheme_atomp(f):
        return False
    else:
        return unify(e.first, f.first, env) and \
               unify(e.second, f.second, env)
```

The `bind` function recursively substitutes all variables with their values until no bound variables remain.

## 4.5.4 Proofs

The logic language functions as a formal system prover where facts establish axioms and queries must be verified from these axioms. Each query asserts an assignment exists where all sub-expressions follow from system facts.

Queries retrieve proofs as traces establishing truth through fact chains.

## 4.5.5 Search

The `search` procedure finds fact chains establishing queries through pattern matching. It recursively processes clauses while managing variable bindings and search depth:

```python
def search(clauses, env, depth):
    """Search for rule applications establishing all CLAUSES,
    non-destructively extending ENV. Limit search to nested
    application of DEPTH rules."""
    if clauses is nil:
        yield env
    elif DEPTH_LIMIT is None or depth <= DEPTH_LIMIT:
        if clauses.first.first in ('not', '~'):
            clause = ground(clauses.first.second, env)
            try:
                next(search(clause, glob, 0))
            except StopIteration:
                env_head = Frame(env)
                for result in search(clauses.second, env_head, depth+1):
                    yield result
        else:
            for fact in facts:
                fact = rename_variables(fact, get_unique_id())
                env_head = Frame(env)
                if unify(fact.first, clauses.first, env_head):
                    for env_rule in search(fact.second, env_head, depth+1):
                        for result in search(clauses.second, env_rule, depth+1):
                            yield result
```

**Unique Names:** Variables across different facts must remain distinct. The `rename_variables` function appends unique identifiers to prevent confusion:

```python
def rename_variables(expr, n):
    """Rename all variables in EXPR with an identifier N."""
    if isvar(expr):
        return expr + '_' + str(n)
    elif scheme_pairp(expr):
        return Pair(rename_variables(expr.first, n),
                    rename_variables(expr.second, n))
    else:
        return expr
```


---

## Same Chapter

- [Ch4 1 Introduction](ch4-1-introduction.md)
- [Ch4 2 Implicit Sequences](ch4-2-implicit-sequences.md)
- [Ch4 3 Declarative Programming](ch4-3-declarative-programming.md)
- [Ch4 4 Logic Programming](ch4-4-logic-programming.md)
- [Ch4 6 Distributed Computing](ch4-6-distributed-computing.md)
- [Ch4 7 Distributed Data Processing](ch4-7-distributed-data-processing.md)
- [Ch4 8 Parallel Computing](ch4-8-parallel-computing.md)
