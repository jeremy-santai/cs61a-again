# Scheme Interpreter Project Summary

**Source Code:**
- [scheme_classes.py](../codebases/scheme_classes.py)
- [scheme_eval_apply.py](../codebases/scheme_eval_apply.py)
- [scheme_forms.py](../codebases/scheme_forms.py)

## Overview

A full interpreter for a subset of the Scheme programming language, implementing the eval-apply cycle, environments, procedures, and special forms.

## Key Concepts Demonstrated

### Interpreter Design (Eval-Apply Cycle)
- **`scheme_eval()`** - Evaluate expressions in an environment
- **`scheme_apply()`** - Apply procedures to arguments
- **`eval_all()`** - Evaluate sequence, return last value

### Environment Model
- **`Frame`** class - Bindings dictionary + parent pointer
- **`lookup()`** - Search current frame, then parent chain
- **`make_child_frame()`** - Create new frame for function calls
- Lexical vs dynamic scoping (Lambda vs Mu procedures)

### Procedure Types

| Type | Scoping | Description |
|------|---------|-------------|
| `BuiltinProcedure` | N/A | Python functions exposed to Scheme |
| `LambdaProcedure` | Lexical | User-defined, captures defining environment |
| `MuProcedure` | Dynamic | Uses calling environment instead |

## Special Forms Implemented

| Form | Purpose |
|------|---------|
| `define` | Bind value or create procedure |
| `lambda` | Create anonymous procedure |
| `if` | Conditional evaluation |
| `and` / `or` | Short-circuit boolean operators |
| `cond` | Multi-way conditional |
| `let` | Local bindings |
| `quote` | Return expression unevaluated |
| `mu` | Dynamic-scoped procedure |

## Key Implementation Details

### Evaluation Rules
- **Symbols** → Look up in environment
- **Self-evaluating** (numbers, booleans) → Return as-is
- **Special forms** → Dispatch to handler function
- **Combinations** → Evaluate operator and operands, then apply

### The Pair Data Structure
- Scheme lists built from `Pair(first, rest)` where rest is Pair or `nil`
- `expr.rest.map(fn)` - Apply function to each element
