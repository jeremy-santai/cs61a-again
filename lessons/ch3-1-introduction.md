# 3.1 Introduction

Chapters 1 and 2 explored the relationship between functions and data, including higher-order functions and message passing. This chapter examines the third programming fundamental: programs themselves.

"A Python program is just a collection of text. Only through the process of interpretation do we perform any meaningful computation based on that text." The core insight is that an interpreter—a program executing evaluation procedures—is itself just another program, representing "the most fundamental idea in programming."

This perspective shifts how programmers view their role: as language designers rather than merely language users.

## 3.1.1 Programming Languages

Programming languages differ significantly in syntax, features, and purpose. General-purpose languages commonly include function definition and application, though powerful languages exist without object systems, higher-order functions, or mutable state.

This chapter introduces Scheme as an example of a minimal yet powerful language. Most interpreters share an elegant structure: two mutually recursive functions—one evaluating expressions in environments, the other applying functions to arguments.


---

## Same Chapter

- [Ch3 2 Functional Programming](ch3-2-functional-programming.md)
- [Ch3 3 Exceptions](ch3-3-exceptions.md)
- [Ch3 4 Interpreters Combination](ch3-4-interpreters-combination.md)
- [Ch3 5 Interpreters Abstraction](ch3-5-interpreters-abstraction.md)
