# 3.4 Interpreters for Languages with Combination

This section explores *metalinguistic abstraction* — the process of creating new programming languages through interpreters. An interpreter is "a function that, when applied to an expression of the language, performs the actions required to evaluate that expression."

The material develops an interpreter for Calculator, a limited Scheme subset supporting arithmetic operations, then sketches a broader Scheme interpreter using the environment model.

## 3.4.1 A Scheme-Syntax Calculator

Calculator is an expression language for arithmetic operations (+, −, ×, ÷) using Scheme's call expression syntax. Addition and multiplication accept arbitrary arguments and have identity elements (0 and 1 respectively). Subtraction and division have dual behaviors based on argument count.

Example evaluation:
```
(- 100 (* 7 (+ 8 (/ -12 -3))))
```
evaluates by recursively processing nested expressions.

## 3.4.2 Expression Trees

Expression trees must be represented as data structures in the program. Primitive expressions are numbers or operator symbols. Combined expressions are call expressions — Scheme lists with an operator followed by zero or more operands.

The **Pair class** represents Scheme pairs and lists in Python, with a corresponding `nil` object for empty lists:

```python
s = Pair(1, Pair(2, nil))
print(s)  # Output: (1 2)
```

Nested pairs represent complex expressions:

```python
expr = Pair('+', Pair(Pair('*', Pair(3, Pair(4, nil))), Pair(5, nil)))
print(expr)  # Output: (+ (* 3 4) 5)
```

## 3.4.3 Parsing Expressions

Parsing converts raw text into expression trees through two components:

**Lexical analysis** tokenizes input strings into minimal syntactic units. The `tokenize_line` function separates symbols and delimiters while converting multi-character numbers:

```python
tokenize_line('(+ 1 (* 2.3 45))')
# Returns: ['(', '+', 1, '(', '*', 2.3, 45, ')', ')']
```

**Syntactic analysis** constructs expression trees from token sequences recursively. The `scheme_read` function processes tokens into Pair structures, with `read_tail` handling list continuation:

```python
lines = ['(+ 1', '   (* 2.3 45))']
expression = scheme_read(Buffer(tokenize_lines(lines)))
print(expression)  # Output: (+ 1 (* 2.3 45))
```

## 3.4.4 Calculator Evaluation

The `calc_eval` function evaluates expressions by dispatching on type:

- **Self-evaluating** expressions (numbers) return directly
- **Call expressions** (Pair instances) recursively evaluate operands, then apply the operator

```python
def calc_eval(exp):
    if type(exp) in (int, float):
        return simplify(exp)
    elif isinstance(exp, Pair):
        arguments = exp.second.map(calc_eval)
        return simplify(calc_apply(exp.first, arguments))
```

The `calc_apply` function implements operator logic for each arithmetic operation, handling argument count requirements and special cases.

### Read-Eval-Print Loops

A REPL provides interactive interpreter access through three steps: reading expressions, evaluating them, and printing results. Error handling allows users to continue after mistakes:

```python
def read_eval_print_loop():
    while True:
        try:
            src = buffer_input()
            while src.more_on_line:
                expression = scheme_read(src)
                print(calc_eval(expression))
        except (SyntaxError, TypeError, ValueError, ZeroDivisionError) as err:
            print(type(err).__name__ + ':', err)
        except (KeyboardInterrupt, EOFError):
            print('Calculation completed.')
            return
```

This structure remains reusable across different language interpreters with parameter adjustments.


---

## Same Chapter

- [Ch3 1 Introduction](ch3-1-introduction.md)
- [Ch3 2 Functional Programming](ch3-2-functional-programming.md)
- [Ch3 3 Exceptions](ch3-3-exceptions.md)
- [Ch3 5 Interpreters Abstraction](ch3-5-interpreters-abstraction.md)
