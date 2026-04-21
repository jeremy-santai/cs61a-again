---
        course: CS61A
        term: Fall 2020
        assessment: MT2
        source_pdf: 61a-fa20-mt2_sol.pdf
        exam_slug: 61a-fa20-mt2
        problem_number: 2
        problem_title: "Yield, Fibonacci!"
        page_range: [5, 8]
        topics: ["higher-order-functions", "generators", "linked-lists", "lists", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 2 — Yield, Fibonacci!

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: MT2
        - Source PDF: `61a-fa20-mt2_sol.pdf`
        - Pages: 5-8

        ## Full extracted content

        ## Page 5

2. (10.0 points)
Yield, Fibonacci!
(a) (4.0 points)
Implement fibs, a generator function that takes a one-argument pure function f and yields all Fibonacci
numbers x for which f(x) returns a true value.
The Fibonacci numbers begin with 0 and then 1. Each subsequent Fibonacci number is the sum of the
previous two. Yield the Fibonacci numbers in order.
def fibs(f):
"""Yield all Fibonacci numbers x for which f(x) is a true value.
>>> odds = fibs(lambda x: x % 2 == 1)
>>> [next(odds) for i in range(10)]
[1, 1, 3, 5, 13, 21, 55, 89, 233, 377]
>>> bigs = fibs(lambda x: x > 20)
>>> [next(bigs) for i in range(10)]
[21, 34, 55, 89, 144, 233, 377, 610, 987, 1597]
>>> evens = fibs(lambda x: x % 2 == 0)
>>> [next(evens) for i in range(10)]
[0, 2, 8, 34, 144, 610, 2584, 10946, 46368, 196418]
"""
n, m = 0, 1
while _________:
(a)
if _________:
(b)
_________
(c)
_________
(d)
i. (1.0 pt) Which of these could fill in blank (a)?
# f(n)
# f(m)
# f(n) or f(m)
# f(n) and f(m)
True
# False

## Page 6

ii. (1.0 pt) Which of these could fill in blank (b)?
f(n)
# f(m)
# f(n) or f(m)
# f(n) and f(m)
# True
# False
iii. (1.0 pt) Fill in blank (c).
yield n
iv. (1.0 pt) Fill in blank (d).
n, m = m, n + m

## Page 7

(b) (6.0 points)
Definition. For a linked list s, the index of an element is the number of times rest appears in the smallest
dot expression containing only s, rest, and first that evaluates to that element. For example, in the
linked list s = Link(5, Link(7, Link(9, Link(11)))),
• The index of 5 (s.first) is 0.
• The index of 7 (s.rest.first) is 1.
• The index of 11 (s.rest.rest.rest.first) is 3.
Implement filter_index, a function that takes a one-argument pure function f and a Link instance s. It
returns a Link containing all elements of s that have an index i for which f(i) returns a true value.
Assume that s is a finite linked list of numbers that contains no repeated elements. The Link class appears
on Page 2 (left column) of the Midterm 2 Study Guide.
def filter_index(f, s):
"""Return a Link containing the elements of Link s that have an index i for
which f(i) is a true value.
>>> powers = Link(1, Link(2, Link(4, Link(8, Link(16, Link(32))))))
>>> filter_index(lambda x: x < 4, powers)
Link(1, Link(2, Link(4, Link(8))))
>>> filter_index(lambda x: x % 2 == 1, powers)
Link(2, Link(8, Link(32)))
"""
def helper(i, s):
if s is Link.empty:
return s
filtered_rest = _________
(a)
if _________:
(b)
return _________
(c)
else:
return filtered_rest
return _________
(d)

## Page 8

i. (1.0 pt) Which of these could fill in blank (a)?
helper(i + 1, s.rest)
# helper(i + 1, s.rest.rest)
# filter_index(f, s.rest)
# filter_index(f, s.rest.rest)
# Link(helper(i + 1, s.rest))
# Link(helper(i + 1, s.rest.rest))
# Link(filter_index(f, s.rest))
# Link(filter_index(f, s.rest.rest))
ii. (1.0 pt) Fill in blank (b).
f(i)
iii. (2.0 pt) Fill in blank (c).
Link(s.first, filtered_rest)
iv. (2.0 pt) Fill in blank (d).
helper(0, s)


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](../61a-fa20-final/p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](../61a-fa20-final/p02-stoned.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](../61a-fa20-final/p03-college-party.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](../61a-fa20-final/p04-last-lecture-ama.md)
- [61a-fa20-final / P05-SCHEMEQL](../61a-fa20-final/p05-schemeql.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](../61a-fa20-mt1/p01-down-for-the-count.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](../61a-fa20-mt1/p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](../61a-fa20-mt1/p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](../61a-fa20-mt1/p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](p01-political-environment.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](p04-fork-it.md)
