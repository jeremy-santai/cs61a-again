# 3.2 Functional Programming

This section introduces a high-level programming language emphasizing functional style. The subset of Scheme discussed "employs a very similar model of computation to Python's, but uses only expressions (no statements), specializes in symbolic computation, and employs only immutable values."

## 3.2.1 Expressions

Scheme programs consist of expressions using call expressions or special forms. Call expressions use prefix notation with operators and operands in parentheses:

```scheme
(quotient 10 2)
(+ (* 3 5) (- 10 6))
```

The **if** special form evaluates predicates and returns consequent or alternative values:

```scheme
(if <predicate> <consequent> <alternative>)
```

Comparison and boolean operations include:

- `(and <e1> ... <en>)` — evaluates left-to-right, returns false on first false value
- `(or <e1> ... <en>)` — evaluates left-to-right, returns first true value
- `(not <e>)` — negation

## 3.2.2 Definitions

Values are named using define:

```scheme
(define pi 3.14)
```

Procedures are defined with:

```scheme
(define (<name> <formal parameters>) <body>)
```

Example functions:

```scheme
(define (square x) (* x x))
(define (average x y) (/ (+ x y) 2))
(define (abs x)
  (if (< x 0) (- x) x))
```

Anonymous functions use lambda:

```scheme
(lambda (<formal-parameters>) <body>)
((lambda (x y z) (+ x y (square z))) 1 2 3)
```

## 3.2.3 Compound Values

Pairs use `cons`, `car`, and `cdr`:

```scheme
(define x (cons 1 2))
(car x)    ; returns 1
(cdr x)    ; returns 2
```

Lists build on pairs using `nil` or `'()` for empty lists:

```scheme
(list 1 2 3 4)
(cons 10 one-through-four)
```

List operations include `null?`, `length`, and `getitem`.

## 3.2.4 Symbolic Data

Quotation prevents evaluation of symbols:

```scheme
(define a 1)
(list 'a 'b)    ; quotes prevent evaluating a and b
(car '(a b c))  ; returns a
```

"Quotation allow us to talk about language itself" through symbolic manipulation.

## 3.2.5 Turtle Graphics

Turtle graphics procedures like `forward` (fd) and `right` (rt) move and draw on canvas. The `begin` special form groups multiple expressions:

```scheme
(define (repeat k fn)
  (if (> k 0)
      (begin (fn) (repeat (- k 1) fn))
      nil))
```

Examples demonstrate drawing stars and Sierpinski's triangle fractals using recursive procedures.


---

## Same Chapter

- [Ch3 1 Introduction](ch3-1-introduction.md)
- [Ch3 3 Exceptions](ch3-3-exceptions.md)
- [Ch3 4 Interpreters Combination](ch3-4-interpreters-combination.md)
- [Ch3 5 Interpreters Abstraction](ch3-5-interpreters-abstraction.md)
