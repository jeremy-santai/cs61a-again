---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 4
problem_title: "Advent of Code"
topics: ["higher-order-functions", "lists", "scheme", "sql"]
---

# Problem 4 — Advent of Code

## Full Extracted Content
## Page 9

4. (16.0 points)
Advent of Code
The choice of programming language can affect the difficulty of implementation. This problem was adapted
from Day 1 of the 2020 Advent of Code, a set of 25 programming challenges released annually in December.
Complete the following Python, Scheme, and SQL solutions to this problem:
Given a list of numbers, find the two numbers in the list that sum to 2020. You are guaranteed that there is
exactly one pair of numbers that sum to 2020 and that the list does not contain 1010.
For example, given [979, 1721, 366, 299, 675, 1456], output [1721, 299], since 1721+299 = 2020.
(a) (5.0 points)
Python
def find_pair(s):
'''Return the two elements of s that sum to 2020, in the order that they appear in s.
>>> find_pair([979, 1721, 366, 299, 675, 1456])
[1721, 299]
'''
for i in __(a)__:
for j in __(b)__:
__(c)__:
return __(d)__
i. (1.0 pt) Fill in Blank (a)
s
# [s]
# s[:len(s)-1]
# zip(s, s)
# range(s)
ii. (1.0 pt) Fill in Blank (b)
# i
# [i]
s
# s[1:]
# range(s)
iii. (2.0 pt) Fill in Blank (c)
if i + j == 2020:
iv. (1.0 pt) Select all expressions that could fill in Blank (d).
■[i, j]
2 list(i, j)
2 [list(i, j)]
2 [next(i), next(j)]

## Page 10

(b) (6.0 points)
Scheme
Implement find-pair in Scheme. You may call contains?, which takes a Scheme list of numbers s and a
number n. It returns whether s contains n.
;;; > (contains? '(1 2 3) 3)
;;; #t
;;; > (contains? '(1 2 3) 4)
;;; #f
(define (contains? s n) ...)
; Assume contains? has been implemented correctly for you.
;;; > (find-pair '(979 1721 366 299 675 1456))
;;; (1721 299)
(define (find-pair s)
(if __(a)__ ( __(b)__ (car s) (- 2020 (car s))) __(c)__ ))
i. (3.0 pt) Fill in Blank (a)
(contains? (cdr s) (- 2020 (car s)))
ii. (1.0 pt) Fill in Blank (b)
# append
# car
# cdr
# cons
list
iii. (2.0 pt) Fill in Blank (c).
# nil
# (cdr s)
# (map (lambda (x) (- 2020 x)) (cdr s))
# (filter (lambda (x) (= 2020 (+ (car s) x))) (cdr s))
(find-pair (cdr s))
# (find-pair (map (lambda (x) (- 2020 x)) (cdr s)))
# (find-pair (filter (lambda (x) (= 2020 (+ (car s) x))) (cdr s)))

## Page 11

(c) (5.0 points)
SQL
Implement a SQL query that creates a one-row, two-column table of numbers where the single row
contains the two numbers in table s that sum to 2020. The order that the numbers appear will not be
graded.
CREATE TABLE s AS
SELECT 979 as num UNION SELECT 1721 UNION SELECT 366 UNION
SELECT 299
UNION SELECT 675
UNION SELECT 1456;
SELECT __(a)__ FROM __(b)__ WHERE __(c)__;
i. (1.0 pt) Fill in Blank (a)
# s, 2020 - s
# num, 2020 - num
# a, b
# s.a, s.b
a.num, b.num
ii. (2.0 pt) Fill in Blank (b)
# s
# a, b
# s, s
s AS a, s AS b
# a AS s, b AS s
iii. (2.0 pt) Fill in Blank (c)
# a + b = 2020
# a.num + b.num = 2020
# a < b AND a + b = 2020
a.num < b.num AND a.num + b.num = 2020
# a = b AND a + b = 2020
# a.num = b.num AND a.num + b.num = 2020
# (2020 - num) IN s
# CONTAINS(2020 - num, s)


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](p03-sum-total.md)
- [61a-fa22-final / P05-TWO-CENTS](p05-two-cents.md)
- [61a-fa22-final / P06-BARKING-UP-THE-WRONG-TREE](p06-barking-up-the-wrong-tree.md)
- [61a-fa22-final / P07-ONE-CENT](p07-one-cent.md)
- [61a-fa22-final / P08-A-PARENTHESES-SCHEME](p08-a-parentheses-scheme.md)
- [61a-fa22-final / P09-POKEMON-SQARLET](p09-pokemon-sqarlet.md)
- [61a-fa22-final / P13-OPTIONAL](p13-optional.md)
- [61a-fa22-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa22-mt1/p01-what-would-python-display.md)
- [61a-fa22-mt1 / P02-DON-T-CALL-ME-I-LL-CALL-YOU](../61a-fa22-mt1/p02-don-t-call-me-i-ll-call-you.md)
- [61a-fa22-mt1 / P03-IT-S-PERFECT](../61a-fa22-mt1/p03-it-s-perfect.md)
- [61a-fa22-mt1 / P04-SUPER-POWERS](../61a-fa22-mt1/p04-super-powers.md)
- [61a-fa22-mt1 / P05-A-QUESTION-1-BUSY-BEAVER](../61a-fa22-mt1/p05-a-question-1-busy-beaver.md)
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](../61a-fa22-mt2/p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](../61a-fa22-mt2/p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](../61a-fa22-mt2/p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](../61a-fa22-mt2/p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](../61a-fa22-mt2/p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](../61a-fa22-mt2/p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](../61a-fa22-mt2/p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](../61a-fa22-mt2/p08-optional.md)
