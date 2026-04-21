# Cats Typing Test Project Summary

**Source Code:** [cats.py](../codebases/cats.py)

## Overview

A typing speed test program that measures words-per-minute (WPM) and accuracy, with autocorrect functionality using edit distance algorithms.

## Key Concepts Demonstrated

### Higher-Order Functions
- **`pick()`** - Selects paragraphs using a predicate function
- **`about()`** - Returns a function that checks if text contains subject words
- **`autocorrect()`** - Uses a diff function parameter to find closest word

### Recursion
- **`feline_fixes()`** - Recursive character substitution counting
- **`minimum_mewtations()`** - Edit distance (Levenshtein) with add/remove/substitute

### Data Abstraction
- **`match()`** - Abstract data type for multiplayer typing matches
- Selectors: `get_word()`, `time()`, `get_all_words()`, `get_all_times()`

## Core Functions

| Function | Purpose |
|----------|---------|
| `pick(paragraphs, select, k)` | Get kth paragraph matching predicate |
| `about(subject)` | Return selector for topic-related paragraphs |
| `accuracy(typed, source)` | Calculate typing accuracy percentage |
| `wpm(typed, elapsed)` | Calculate words per minute |
| `autocorrect()` | Find closest word within edit limit |
| `feline_fixes()` | Count substitutions needed (simple diff) |
| `minimum_mewtations()` | Full edit distance calculation |

## Edit Distance Algorithm
The `minimum_mewtations` function implements classic edit distance:
- **Add** - Insert character from source
- **Remove** - Delete character from typed
- **Substitute** - Replace character
- Returns minimum operations to transform typed → source
