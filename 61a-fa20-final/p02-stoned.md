---
        course: CS61A
        term: Fall 2020
        assessment: Final
        source_pdf: 61a-fa20-final_sol.pdf
        exam_slug: 61a-fa20-final
        problem_number: 2
        problem_title: "Stoned"
        page_range: [5, 8]
        topics: ["higher-order-functions", "recursion"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 2 — Stoned

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: Final
        - Source PDF: `61a-fa20-final_sol.pdf`
        - Pages: 5-8

        ## Full extracted content

        ## Page 5

2. (16.0 points)
Stoned
Definition: A hailstone sequence begins with a positive integer n. If n is even, divide it by 2. If n is odd, triple
it and add 1. Repeat until 1 is reached. For example, the hailstone sequence starting at 10 is 10, 5, 16, 8, 4, 2, 1.
Assume that all hailstone sequences are finite.
(a) (9.0 points)
Implement hailstone, which takes a positive integer n and a one-argument function g. It calls g on each
element of the hailstone sequence starting at n and returns the length of the sequence.
def hailstone(n, g):
"""Call g on each element of the hailstone sequence starting
at n and return its length.
>>> a = hailstone(10, print)
>>> a
>>> s = []
>>> hailstone(10, s.append)
>>> s
[10, 5, 16, 8, 4, 2, 1]
"""
if n == 1:
h = _________
#
(a)
elif _________:
#
(b)
h = up
else:
h = down
_________
#
(c)
return _________(n, _________)
#
(d)
(e)
def up(n, f):
return 1 + f(3 * n + 1)
def down(n, f):

## Page 6

return 1 + f(n // 2)
i. (2.0 pt) Fill in blank (a)?
lambda n, f: 1
ii. (2.0 pt) Fill in blank (b)?
n % 2 == 1
iii. (2.0 pt) Fill in blank (c)?
g(n)
iv. (1.0 pt) Which of these could fill in blank (d)?
# f
# g
h
# hailstone
# up
# down
v. (2.0 pt) Fill in blank (e)?
lambda n: hailstone(n, g)

## Page 7

(b) (7.0 points)
Implement collide, which takes positive integers m and n. It returns the earliest element of the hailstone
sequence starting at n that also appears in the hailstone sequence starting at m. Assume hailstone is
implemented correctly.
def collide(m, n):
"""Return the earliest number in the hailstone sequence starting at n that
also appears in the hailstone sequence starting at m.
>>> collide(10, 32)
# 10, 5, 16, 8, ...
vs
32, 16, 8, ...
>>> collide(13, 11)
# 13, 40, ...
vs
11, 34, 17, 52, 26, 13, 40, ...
"""
s = []
hailstone(m, _________)
#
(a)
found = None
def f(k):
_________
#
(b)
if _________:
#
(c)
_________
#
(d)
hailstone(n, f)
return _________
#
(e)
i. (2.0 pt) Fill in blank (a)?
s.append
ii. (1.0 pt) Fill in blank (b)?
nonlocal found
iii. (2.0 pt) Fill in blank (c)?
found is None and k in s

## Page 8

iv. (1.0 pt) Which of the these could fill in blank (d)?
found = k
# found = min(k, n)
# return k
# return min(k, n)
# found.append(k)
# found.append(min(k, n))
v. (1.0 pt) Which of the these could fill in blank (e)?
found
# found[0]
# found[-1]
# f(m)
# f(n)
# s
# s[0]
# s[-1]


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](p03-college-party.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](p04-last-lecture-ama.md)
- [61a-fa20-final / P05-SCHEMEQL](p05-schemeql.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](../61a-fa20-mt1/p01-down-for-the-count.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](../61a-fa20-mt1/p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](../61a-fa20-mt1/p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](../61a-fa20-mt1/p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](../61a-fa20-mt2/p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](../61a-fa20-mt2/p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](../61a-fa20-mt2/p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](../61a-fa20-mt2/p04-fork-it.md)
