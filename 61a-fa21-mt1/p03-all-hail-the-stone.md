---
        course: CS61A
        term: Fall 2021
        assessment: MT1
        source_pdf: 61a-fa21-mt1_sol.pdf
        exam_slug: 61a-fa21-mt1
        problem_number: 3
        problem_title: "All Hail the Stone"
        page_range: [7, 14]
        topics: ["higher-order-functions", "recursion"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 3 — All Hail the Stone

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: MT1
        - Source PDF: `61a-fa21-mt1_sol.pdf`
        - Pages: 7-14

        ## Full extracted content

        ## Page 7

3. (27.0 points)
All Hail the Stone
Definition: A hailstone sequence begins with a positive integer n. If n is even, divide it by 2. If n is odd, triple
it and add 1. Repeat until 1 is reached. For example, the hailstone sequence starting at 3 is 3, 10, 5, 16, 8, 4, 2,
1. Assume all hailstone sequences are finite and end with 1.
Assume the following code has been executed.
from operator import add, mul
def next_hail(k):
"""Return the next element in a hailstone sequence."""
assert k > 1
if k % 2 == 0:
return k // 2
else:
return 3 * k + 1
(a) (8.0 points)
Implement hail_min, which takes a positive integer n and a one-argument function measure. It returns
the element of the hailstone sequence starting with n for which calling measure on the element returns the
smallest value.
If more than one element of the sequence has the smallest measure value, return the earliest one.
def hail_min(n, measure):
"""Return the element k of the hailstone sequence starting with n for which
measure(k) is smallest. In case of a tie, return the earliest element.
>>> hail_min(5, lambda k: -k)
# Among 5, 16, 8, 4, 2, 1; 16 is largest
>>> hail_min(8, lambda k: -k)
# Among 8, 4, 2, 1; 8 is largest
>>> hail_min(3, lambda k: abs(k - 7))
# Among 3, 10, 5, 16, 8, 4, 2, 1; 8 is closest to 7
>>> hail_min(9, lambda k: abs(k - 7))
# Among 9, 28, 14, 7, 22, ...; 7 is closest to 7
>>> hail_min(8, lambda k: abs(k - 3))
# 4 and 2 are both close to 3, but 4 is earliest
"""
apple = _________
(a)
while n > 1:
n = next_hail(n)
if _________:
(b)
_________
(c)
return _________
(d)

## Page 8

i. (1.0 pt) Fill in blank (a).
n
ii. (3.0 pt) Fill in blank (b).
measure(n) < measure(apple)
iii. (1.0 pt) Fill in blank (c).
apple = n
iv. (1.0 pt) Which of these could fill in blank (d)? Check all that apply.
2 n
■apple
2 measure(n)
2 measure(apple)
2 min(n, apple)
2 min(measure(n), measure(apple))
v. (2.0 pt) What element of the hailstone sequence starting with n larger than 1 is returned by the
expression:
hail_min(n, lambda k: 1 - k % 2)
# Always n (the first element)
# Always 1 (the last element)
# The largest odd element
# The largest even element
# The smallest odd element
# The smallest even element
The first odd element
# The first even element

## Page 9

(b) (6.0 points)
Definition: An accumulator function is a function that takes two integers and returns an integer. It can
serve as the second argument to hail_tally below.
def hail_tally(n, f):
"""Accumulate the elements of the hailstone sequence starting with n using
accumulator function f.
>>> hail_tally(3, add)
# 3 + 10 + 5 + 16 + 8 + 4 + 2 + 1 = 49
>>> hail_tally(10, max)
# Largest of 10, 5, 16, 8, 4, 2, 1
"""
total = 0
while n > 1:
total = f(total, n)
n = next_hail(n)
return f(total, 1)
Implement sum_some, which takes a one-argument function select and returns an accumulator function
f. For positive integer n, the call hail_tally(n, f) returns the sum of the elements of the hailstone
sequence starting with n for which calling select on the element returns a true value.
def sum_some(select):
"""Return an accumulator function that sums all k for which select(k) is a true value.
>>> def below_ten(k):
...
return k < 10
>>> sum_below_ten = sum_some(below_ten)
>>> hail_tally(3, sum_below_ten)
# [3] + 10 + [5] + 16 + [8] + [4] + [2] + [1]
"""
def f(total, k):
if _________:
(a)
return _________(total, k)
(b)
return _________
(c)
_________
(d)
i. (2.0 pt) Fill in blank (a).
select(k)

## Page 10

ii. (1.0 pt) Which of these could fill in blank (b)? Check all that apply.
■add
2 mul
2 sum_some
2 total
2 f
2 hail_tally
iii. (1.0 pt) Which of these could fill in blank (c)?
# k
total
# total + k
# hail_tally(k, sum_some)
# hail_tally(total, sum_some)
# hail_tally(total + k, sum_some)
iv. (2.0 pt) Fill in blank (d).
return f

## Page 11

(c) (5.0 points)
Implement hail_odd_sum, a function that takes a positive integer n and returns the sum of all odd elements
in the hailstone sequences starting with n.
Important: Your solution must include sum_some.
You may also call other functions defined previously in this question.
def hail_odd_sum(n):
"""Sum the odd elements of the hailstone sequence starting with n.
>>> hail_odd_sum(3)
# [3], 10, [5], 16, 8, 4, [1]; 3 + 5 + 1 = 9
>>> hail_odd_sum(34)
# 34, [17], 52, 26, [13], 40, 20, 10, [5], ..., [1]
"""
return _________(_________, _________)
(a)
(b)
(c)
i. (1.0 pt) Fill in blank (a).
hail_tally
ii. (1.0 pt) Fill in blank (b).
n
iii. (3.0 pt) Fill in blank (c).
sum_some(lambda k: k % 2 == 1)

## Page 12

(d) (8.0 points)
Definition: To call a function f repeatedly on a sequence of values x, y, z means to use f in a nested call
expression in which each element of the sequence is passed in as a single argument in order: f(x)(y)(z).
Implement hail, which takes an integer n greater than 1. It returns a function that returns True when
called repeatedly on all of the remaining elements of the hailstone sequence starting with n. It returns
False when called repeatedly on any sequence that differs from the hailstone sequence starting with n.
Hint: You may call next_hail (and other functions defined previously in this question).
def hail(n):
"""Return a function that returns True if called repeatedly on the remaining
elements of the hailstone sequence starting with n and False otherwise.
>>> hail(3)(10)(5)(16)(8)(4)(2)(1)
True
>>> hail(3)(4)
# The next element should have been 10.
False
>>> hail(3)(10)(5)(16)(8)(1)
# The next element should have been 4.
False
"""
assert n > 1
def check(k):
if _________:
(a)
return True
if _________:
(b)
return False
return _________
(c)
return _________
(d)
i. (2.0 pt) Fill in blank (a).
n == 2 and k == 1
ii. (2.0 pt) Fill in blank (b).
next_hail(n) != k

## Page 13

iii. (2.0 pt) Fill in blank (c).
hail(k)
iv. (2.0 pt) Fill in blank (d).
check

## Page 14

No more questions.


---

## Same Semester

- [61a-fa21-final / P01-HOUSE-ATREIDES](../61a-fa21-final/p01-house-atreides.md)
- [61a-fa21-final / P02-ARRAKIS](../61a-fa21-final/p02-arrakis.md)
- [61a-fa21-final / P03-CALADAN](../61a-fa21-final/p03-caladan.md)
- [61a-fa21-final / P04-SPICE](../61a-fa21-final/p04-spice.md)
- [61a-fa21-final / P05-GOM-JABBAR](../61a-fa21-final/p05-gom-jabbar.md)
- [61a-fa21-final / P06-JUST-FOR-FUN](../61a-fa21-final/p06-just-for-fun.md)
- [61a-fa21-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa21-mt1 / P02-31-CAL-OLYMPIANS](p02-31-cal-olympians.md)
- [61a-fa21-mt2 / P01-HAWKEYE](../61a-fa21-mt2/p01-hawkeye.md)
- [61a-fa21-mt2 / P02-DOCTOR-CHANGE](../61a-fa21-mt2/p02-doctor-change.md)
- [61a-fa21-mt2 / P03-SHANG-CHI](../61a-fa21-mt2/p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](../61a-fa21-mt2/p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](../61a-fa21-mt2/p05-groot.md)
