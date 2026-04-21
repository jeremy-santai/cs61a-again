---
        course: CS61A
        term: Fall 2020
        assessment: MT1
        source_pdf: 61a-fa20-mt1_sol.pdf
        exam_slug: 61a-fa20-mt1
        problem_number: 2
        problem_title: "Mystery Function"
        page_range: [9, 10]
        topics: ["higher-order-functions", "combinatorics"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 2 — Mystery Function

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: MT1
        - Source PDF: `61a-fa20-mt1_sol.pdf`
        - Pages: 9-10

        ## Full extracted content

        ## Page 9

2. (8.0 points)
Mystery Function
Assume mystery is a deterministic pure function that takes one integer argument, returns an integer, and never
errors.
def mystery(n):
...
Assume the following functions are also defined:
def add_two(y):
return y + 2
def two(y):
return 2
def constant(k):
def ignore(x):
return k
return ignore
def diff(f, g):
return lambda z: abs(f(z) - g(z))
Definition. Two functions f and g have identical behavior if f(x) and g(x) return equal values or return
functions with identical behavior, for every x that does not cause an error.
Complete each statement below so that it is true for all possible deterministic pure mystery functions.
(a) (2.0 pt) The result of evaluating constant(2) has identical behavior to the result of evaluating the
expression. . .
# . . . add_two
# . . . add_two(0)
# . . . add_two(2)
. . . two
# . . . two(0)
# . . . two(2)
# None of these
(b) (2.0 pt) The result of evaluating diff(constant(1), constant(-1)) has identical behavior to the result
of evaluating the expression. . .
# . . . constant
# . . . constant(0)
. . . constant(2)
# . . . diff(constant, constant)
# None of these

## Page 10

(c) (2.0 pt) The result of evaluating diff(mystery, mystery) has identical behavior to the result of
evaluating the expression. . .
# . . . constant
. . . constant(0)
# . . . constant(2)
# . . . diff(constant, constant)
# . . . constant(mystery)
# . . . mystery
# None of these
(d) (2.0 pt) The result of evaluating diff(mystery, diff(mystery, mystery)) has identical behavior to
the result of evaluating the expression. . .
# . . . mystery
# . . . abs(mystery)
. . . lambda y: abs(mystery(y))
# . . . lambda y: mystery(abs(y))
# . . . lambda y: lambda z: mystery(abs(y)) - mystery(abs(z))
# . . . lambda y: lambda z: abs(mystery(y)) - abs(mystery(z))
# . . . lambda y: lambda z: abs(mystery(y) - mystery(z))
# None of these


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](../61a-fa20-final/p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](../61a-fa20-final/p02-stoned.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](../61a-fa20-final/p03-college-party.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](../61a-fa20-final/p04-last-lecture-ama.md)
- [61a-fa20-final / P05-SCHEMEQL](../61a-fa20-final/p05-schemeql.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](p01-down-for-the-count.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](../61a-fa20-mt2/p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](../61a-fa20-mt2/p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](../61a-fa20-mt2/p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](../61a-fa20-mt2/p04-fork-it.md)
