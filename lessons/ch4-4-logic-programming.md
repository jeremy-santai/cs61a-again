# 4.4 Logic Programming

This section introduces a declarative query language called logic, inspired by Prolog and concepts from "Structure and Interpretation of Computer Programs." The language uses Scheme lists for data records and Scheme values for queries, with a complete interpreter implementation.

## 4.4.1 Facts and Queries

**Basic Concepts**

Facts represent relationships in a database. A fact statement uses the keyword `fact` followed by one or more lists. For example:

```
(fact (parent abraham barack))
(fact (parent abraham clinton))
```

These declare relations rather than procedure applications. Relations don't require advance definition and are matched against queries rather than applied.

Queries retrieve matching facts using the keyword `query` and may contain variables (symbols beginning with `?`):

```
(query (parent abraham ?child))
```

**Compound Facts**

Multi-expression facts have a conclusion followed by hypotheses. The conclusion is true only if all hypotheses are satisfied:

```
(fact <conclusion> <hypothesis0> <hypothesis1> ... <hypothesisN>)
```

For instance: `(fact (child ?c ?p) (parent ?p ?c))` means "?c is a child of ?p if ?p is the parent of ?c."

**Negation**

The keyword `not` enables negation-as-failure queries:

```
(query (not (parent abraham clinton)))
```

A query succeeds if its relation fails, and fails if the relation succeeds. This approach can be counterintuitive—`(query (not (parent abraham ?who)))` fails because the relation succeeds for multiple bindings.

## 4.4.2 Recursive Facts

Recursive facts allow conclusions to depend on hypotheses containing the same symbols. The ancestor relation uses two facts:

```
(fact (ancestor ?a ?y) (parent ?a ?y))
(fact (ancestor ?a ?y) (parent ?a ?z) (ancestor ?z ?y))
```

**Compound Queries**

Multiple subexpressions in a query must all be satisfied simultaneously, and variables appearing multiple times must have identical values:

```
(query (ancestor ?a barack) (ancestor ?a herbert))
```

**Hierarchical Facts**

Facts and queries can contain nested lists for representing structured data:

```
(fact (dog (name abraham) (color white)))
(query (dog (name clinton) (color ?color)))
```

Dotted list notation matches variable-length tails:

```
(fact (pedigree ?name) (dog (name ?name) . ?details))
```

**Practical Example: List Append**

Two facts define appending lists:

```
(fact (append-to-form () ?x ?x))
(fact (append-to-form (?a . ?r) ?y (?a . ?z)) (append-to-form ?r ?y ?z))
```

The interpreter can compute append results or find all pairs of lists forming a target list through repeated list-matching operations.


---

## Same Chapter

- [Ch4 1 Introduction](ch4-1-introduction.md)
- [Ch4 2 Implicit Sequences](ch4-2-implicit-sequences.md)
- [Ch4 3 Declarative Programming](ch4-3-declarative-programming.md)
- [Ch4 5 Unification](ch4-5-unification.md)
- [Ch4 6 Distributed Computing](ch4-6-distributed-computing.md)
- [Ch4 7 Distributed Data Processing](ch4-7-distributed-data-processing.md)
- [Ch4 8 Parallel Computing](ch4-8-parallel-computing.md)
