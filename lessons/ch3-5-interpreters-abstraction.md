# 3.5 Interpreters for Languages with Abstraction

This section addresses how to build a Scheme interpreter that supports abstraction—enabling programmers to define new operations and bind names to values. Unlike the Calculator language from section 3.4, which lacks abstraction capabilities, Scheme allows for more general and powerful programming through user-defined functions and symbolic naming.

## 3.5.1 Structure

The Scheme interpreter shares architectural similarities with the Calculator interpreter, featuring a parser that produces expressions and an evaluator that interprets them.

**Parsing Requirements**

The existing `scheme_reader` and `scheme_tokens` modules require extension to support quotation and dotted lists. For example:

```python
>>> read_line("(car '(1 . 2))")
Pair('car', Pair(Pair('quote', Pair(Pair(1, 2), nil)), nil))
```

**Evaluation Process**

The `scheme_eval` function processes three expression types: primitives, special forms, and call expressions. A simplified implementation:

```python
def scheme_eval(expr, env):
    """Evaluate Scheme expression expr in environment env."""
    if scheme_symbolp(expr):
        return env[expr]
    elif scheme_atomp(expr):
        return expr
    first, rest = expr.first, expr.second
    if first == "lambda":
        return do_lambda_form(rest, env)
    elif first == "define":
        do_define_form(rest, env)
        return None
    else:
        procedure = scheme_eval(first, env)
        args = rest.map(lambda operand: scheme_eval(operand, env))
        return scheme_apply(procedure, args, env)
```

**Procedure Application**

The `scheme_apply` function handles two procedure types:

- **PrimitiveProcedure**: Implemented in Python with a bound function
- **LambdaProcedure**: Implemented in Scheme; its body is evaluated in a new environment extending the procedure's parent environment, with formal parameters bound to arguments

**Eval/Apply Recursion**

"Evaluation requires application whenever a call expression is encountered. Application uses evaluation to evaluate operand expressions into arguments, as well as to evaluate the body of user-defined procedures." This mutual recursion terminates with primitive evaluations and primitive procedure applications.

## 3.5.2 Environments

Each `Frame` instance represents an environment binding symbols to values. Frames maintain a parent reference (None for the global frame) and provide two key methods:

- **lookup**: Searches current frame for a symbol; if not found, proceeds to parent frame
- **define**: Binds a symbol to a value in the current frame

**Example: Factorial Definition**

```scheme
(define (factorial n)
  (if (= n 0) 1 (* n (factorial (- n 1)))))
```

When defining a function:

1. Validate the expression format
2. Extract function name and formal parameters
3. Create a LambdaProcedure with body and parent environment
4. Bind the symbol in the current frame

On invocation with argument 5, a new frame extends the global frame with n bound to 5, then evaluates the body in that environment.

## 3.5.3 Data as Programs

The Scheme interpreter functions as a universal machine that configures itself to emulate any machine described as a Scheme program. A factorial procedure can be equivalently expressed in Python:

```python
def factorial(n):
    return 1 if n == 1 else n * factorial(n - 1)
```

User-supplied programs constitute data that the interpreter manipulates according to defined rules. Many dynamic languages support explicit evaluation of constructed expressions—Python's `eval()` and `exec()` functions exemplify this capability, enabling powerful metaprogramming techniques.


---

## Same Chapter

- [Ch3 1 Introduction](ch3-1-introduction.md)
- [Ch3 2 Functional Programming](ch3-2-functional-programming.md)
- [Ch3 3 Exceptions](ch3-3-exceptions.md)
- [Ch3 4 Interpreters Combination](ch3-4-interpreters-combination.md)
