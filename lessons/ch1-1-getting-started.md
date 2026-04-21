# 1.1 Getting Started

Computer science spans numerous disciplines including distributed systems, artificial intelligence, robotics, graphics, security, and scientific computing. The field's rapid advancement relies on fundamental concepts: representing information, specifying processing logic, and designing abstractions to manage complexity.

These materials build upon _Structure and Interpretation of Computer Programs_ (SICP), adapted under Creative Commons licensing. The content emphasizes understanding how computers execute programs and perform computational processes.

## 1.1.1 Programming in Python

> "A language isn't something you learn so much as something you join."

Python serves as the primary language for this text. It attracts developers from web programming, game development, science, academia, and language design. The Python community comprises millions of developers who collaborate on problem-solving and tool development.

Created by Guido van Rossum in the late 1980s, Python emphasizes human-readable code guided by principles of beauty, simplicity, and readability. Its flexibility supports various programming styles and paradigms, making it suitable for both instruction and practical application across thousands of active projects.

## 1.1.2 Installing Python 3

This text uses the most recent stable Python 3 version. While many computers have older versions (like Python 2.7), they won't align with these materials. Python 3 is freely available from the official downloads page.

## 1.1.3 Interactive Sessions

Interactive Python sessions allow you to type code after the `>>>` prompt, which the interpreter reads and executes. Start a session by running the Python 3 application or typing `python3` at a terminal.

Navigation controls include:
- `<Control>-P` for previous history
- `<Control>-N` for next history
- `<Control>-D` to exit
- Up/down arrows for history cycling

## 1.1.4 First Example

Python provides built-in support for text manipulation, graphics, and internet communication. The statement `from urllib.request import urlopen` imports internet data access functionality.

**Statements & Expressions**: Programs consist of instructions that either compute values or perform actions. Statements describe actions; expressions describe computations. When evaluated, expressions produce values.

The assignment statement `shakespeare = urlopen('http://composingprograms.com/shakespeare.txt')` associates a name with a value—here, the complete text of Shakespeare's 37 plays.

**Functions**: Functions encapsulate logic that manipulates data. The `urlopen` function processes a web address to retrieve Shakespeare's works.

The statement `words = set(shakespeare.read().decode().split())` creates a set of all 33,721 unique words appearing in the plays.

**Objects**: Sets bundle data with manipulating logic. The expression:

```python
{w for w in words if len(w) == 6 and w[::-1] in words}
```

produces words that are valid when reversed: `{'redder', 'drawer', 'reward', 'diaper', 'repaid'}`. The notation `w[::-1]` reverses word letters.

**Interpreters**: Evaluating complex expressions requires precise interpretation procedures. Python's flexibility enables processing large text volumes with minimal code.

Functions, objects, and interpreters interconnect: functions are objects, objects are functions, and interpreters exemplify both concepts.

## 1.1.5 Errors

Experimentation is encouraged, but errors will occur. Computers are described as:

> "very powerful, looking at volumes of data very quickly" yet "shockingly stupid and fragile."

Operations must be exact—minor spelling or formatting changes cause unexpected behavior.

**Debugging** involves interpreting errors and diagnosing unexpected results. Key principles:

1. **Test incrementally**: Compose programs from testable components; verify immediately
2. **Isolate errors**: Trace problems to the smallest code fragment
3. **Check assumptions**: Verify that code behaves as expected
4. **Consult others**: Seek help from peers, instructors, or search resources


---

## Same Chapter

- [Ch1 2 Elements Of Programming](ch1-2-elements-of-programming.md)
- [Ch1 3 Defining New Functions](ch1-3-defining-new-functions.md)
- [Ch1 4 Designing Functions](ch1-4-designing-functions.md)
- [Ch1 5 Control](ch1-5-control.md)
- [Ch1 6 Higher Order Functions](ch1-6-higher-order-functions.md)
- [Ch1 7 Recursive Functions](ch1-7-recursive-functions.md)
