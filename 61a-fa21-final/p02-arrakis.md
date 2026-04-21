---
        course: CS61A
        term: Fall 2021
        assessment: Final
        source_pdf: 61a-fa21-final_sol.pdf
        exam_slug: 61a-fa21-final
        problem_number: 2
        problem_title: "Arrakis"
        page_range: [7, 15]
        topics: ["higher-order-functions", "generators", "linked-lists", "lists", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 2 — Arrakis

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: Final
        - Source PDF: `61a-fa21-final_sol.pdf`
        - Pages: 7-15

        ## Full extracted content

        ## Page 7

2. (28.0 points)
Arrakis
Definition. A worm is a non-negative integer in which the absolute difference between each pair of adjacent
digits is 1. 4345 is a worm. 4334 and 4354 are not. All non-negative integers below 10 are worms.
You may use near in the problems below.
def near(i, j):
"""Return whether digits i and j have absolute difference equal to 1."""
assert i >= 0 and i < 10 and j >= 0 and j < 10
return abs(i - j) == 1
(a) (4.0 points)
Implement is_worm, which takes a non-negative integer n and returns True if n is a worm and False
otherwise.
def is_worm(n):
"""Return whether non-negative n is a worm.
>>> [is_worm(0), is_worm(4), is_worm(4345), is_worm(4334), is_worm(4354)]
[True, True, True, False, False]
>>> [n for n in range(200, 300) if is_worm(n)]
[210, 212, 232, 234]
"""
if _________:
(a)
_________
(b)
return near(n % 10, _________) and is_worm(_________)
(c)
(d)
i. (1.0 pt) Which of these could fill in blank (a)?
# n == 0
# n <= 0
n < 10
# n > 0 and n < 10
ii. (1.0 pt) Fill in blank (b).
return True

## Page 8

iii. (1.0 pt) Which of these could fill in blank (c)?
# n % 10
# n // 10
# n % 100
# n // 100
# (n % 10) // 10
(n // 10) % 10
# (n % 10) // 100
# (n // 100) % 10
iv. (1.0 pt) Which of these could fill in blank (d)?
# n % 10
n // 10
# n % 100
# n // 100
# (n % 10) // 10
# (n // 10) % 10
# (n % 10) // 100
# (n // 100) % 10

## Page 9

(b) (7.0 points)
Implement sandworm, which takes a non-negative integer n and returns the largest worm that appears
among the digits of n in order (but not necessarily formed of adjacent digits).
A worm a is larger than a worm b if a > b. Worms are integers.
def sandworm(n):
"""Return the largest worm formed by selecting some digits of non-negative n.
>>> sandworm(13531)
# 13[5]31
>>> sandworm(152)
# [1]5[2]
>>> sandworm(31415926535)
# [3]1[4]1[5]92[6]53[5]
>>> sandworm(314159265358973)
# [3]1[4]1[5]92[6]53589[7]3
"""
if n == 0:
return 0
def use_last(n):
"Return the largest worm in n that includes n % 10"
return tooth(n // 10, n % 10)
def tooth(n, d):
"Return the largest worm formed by some digits of n followed by digit d."
if n == 0:
return _________
(a)
skip = _________
(b)
if near(n % 10, d):
return max(skip, _________)
(c)
else:
return skip
return max(_________, use_last(n))
(d)
i. (2.0 pt) Fill in blank (a).
d

## Page 10

ii. (2.0 pt) Fill in blank (b).
tooth(n // 10, d)
iii. (2.0 pt) Which of these could fill in blank (c)?
# 10 * use_last(n) + n % 10
# 10 * use_last(n // 10) + n % 10
# 10 * sandworm(n) + n % 10
# 10 * sandworm(n // 10) + n % 10
10 * use_last(n) + d
# 10 * use_last(n // 10) + d
# 10 * sandworm(n) + d
# 10 * sandworm(n // 10) + d
iv. (1.0 pt) Which of these could fill in blank (d)?
sandworm(n // 10)
# use_last(n // 10)
# tooth(n // 10, 0)
# 10 * sandworm(n // 10) + n % 10
# 10 * use_last(n // 10) + n % 10
# 10 * tooth(n // 10, 0) + n % 10

## Page 11

(c) (7.0 points)
Implement thumper, a generator function that takes a positive integer k and a digit m. It yields all k-digit
worms with digits that are all less than or equal to m, and it yields these results in increasing order. Assume
the number 0 has 0 digits.
def thumper(k, m):
"""Yield all k-digit worms with digits that are at most m, in increasing order.
>>> list(thumper(1, 7))
# Note: 0 has no digits, so it is not a 1-digit worm.
[1, 2, 3, 4, 5, 6, 7]
>>> list(thumper(2, 3))
[10, 12, 21, 23, 32]
>>> list(thumper(3, 3))
[101, 121, 123, 210, 212, 232, 321, 323]
"""
if k == 1:
_________
(a)
else:
for w in _________:
(b)
if _________:
(c)
yield 10 * w + (w % 10 - 1)
if _________:
(d)
yield 10 * w + (w % 10 + 1)
i. (3.0 pt) Fill in blank (a).
yield from range(1, m + 1)
ii. (2.0 pt) Fill in blank (b).
thumper(k-1, m)

## Page 12

iii. (1.0 pt) Which of these could fill in blank (c)?
# True
# False
# w > 0
# w >= 0
# w < m
# w <= m
w % 10 > 0
# w % 10 >= 0
# w % 10 < m
# w % 10 <= m
iv. (1.0 pt) Which of these could fill in blank (d)?
# True
# False
# w > 0
# w >= 0
# w < m
# w <= m
# w % 10 > 0
# w % 10 >= 0
w % 10 < m
# w % 10 <= m

## Page 13

(d) (8.0 points)
Implement segment, which takes a positive integer n (such as 3456) and a two-argument function grouped.
It returns a linked list s containing linked lists of digits (such as <<3 4> <5 6>>). Together, the elements
of s contain all digits of n in order. Two adjacent digits a and b (with a to the left of b) appear in the
same element of s if grouped(a, b) returns a true value.
The Link class appears on page 2 (left column) of the midterm 2 study guide.
def segment(n, grouped):
"""Return a linked list of linked lists of the digits of positive n.
Adjacent digits a and b appear in the same linked list if grouped(a, b).
>>> print(segment(3233344, lambda a, b: a == b))
<<3> <2> <3 3 3> <4 4>>
>>> print(segment(314159, lambda a, b: a == 1))
<<3> <1 4> <1 5> <9>>
"""
part = Link.empty
parts = Link.empty
while n:
if part is Link.empty or _________:
(a)
_________
(b)
else:
_________
(c)
part = _________
(d)
_________
(e)
return _________
(f)
i. (2.0 pt) Fill in blank (a).
grouped(n % 10, part.first)

## Page 14

ii. (2.0 pt) Which of these could fill in blank (b)?
# part = Link(n, part)
part = Link(n % 10, part)
# part = Link(n // 10 % 10, part)
# part.rest = Link(n)
# part.rest = Link(n % 10)
# part.rest = Link(n // 10 % 10)
iii. (1.0 pt) Which of these could fill in blank (c)?
# parts.append(part)
# parts.rest = Link(part)
parts = Link(part, parts)
# parts = part + parts
# parts += part
# parts += Link(part)
iv. (1.0 pt) Which of these could fill in blank (d)?
# part.first
# part.rest
# Link.empty
Link(n % 10)
# Link(n, part)
# Link(n % 10, part)
v. (1.0 pt) Fill in blank (e).
n = n // 10
vi. (1.0 pt) Fill in blank (f).
Link(part, parts)

## Page 15

(e) (2.0 points)
Implement desert, which takes a positive integer n. It returns a linked list s containing linked lists of
digits. Together, the elements of s contain all digits of n in order, and s is the shortest linked list for
which each element contains the digits of a worm. Assume that segment is implemented correctly.
def desert(n):
"""Return the shortest linked list whose elements are linked lists
of digits of worms that together are the digits of positive n.
>>> print(desert(43587))
<<4 3> <5> <8 7>>
>>> print(desert(11235813213455))
<<1> <1 2 3> <5> <8> <1> <3 2 1> <3 4 5> <5>>
"""
return _________
(a)
i. (2.0 pt) Fill in blank (a).
segment(n, near)


---

## Same Semester

- [61a-fa21-final / P01-HOUSE-ATREIDES](p01-house-atreides.md)
- [61a-fa21-final / P03-CALADAN](p03-caladan.md)
- [61a-fa21-final / P04-SPICE](p04-spice.md)
- [61a-fa21-final / P05-GOM-JABBAR](p05-gom-jabbar.md)
- [61a-fa21-final / P06-JUST-FOR-FUN](p06-just-for-fun.md)
- [61a-fa21-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa21-mt1/p01-what-would-python-display.md)
- [61a-fa21-mt1 / P02-31-CAL-OLYMPIANS](../61a-fa21-mt1/p02-31-cal-olympians.md)
- [61a-fa21-mt1 / P03-ALL-HAIL-THE-STONE](../61a-fa21-mt1/p03-all-hail-the-stone.md)
- [61a-fa21-mt2 / P01-HAWKEYE](../61a-fa21-mt2/p01-hawkeye.md)
- [61a-fa21-mt2 / P02-DOCTOR-CHANGE](../61a-fa21-mt2/p02-doctor-change.md)
- [61a-fa21-mt2 / P03-SHANG-CHI](../61a-fa21-mt2/p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](../61a-fa21-mt2/p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](../61a-fa21-mt2/p05-groot.md)
