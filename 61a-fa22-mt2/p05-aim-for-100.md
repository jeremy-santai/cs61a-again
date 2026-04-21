---
course: CS61A
term: Fall 2022
assessment: MT2
exam_slug: 61a-fa22-mt2
problem_number: 5
problem_title: "Aim for 100"
topics: ["lists"]
---

# Problem 5 — Aim for 100

## Full Extracted Content
## Page 12

5. (7.0 points)
Aim for 100
The function count_subsets takes as input a list of positive integers s. It returns the number of lists that sum
to 100 and contain a subset of the elements of s in order.
def count_subsets(s):
"""
>>> count_subsets([25, 50, 75, 100, 125, 150])
# [25, 75], [100]
>>> count_subsets([25, 50, 25, 75])
# [25, 75] (first 25), [25, 75] (second 25), [25, 50, 25]
>>> count_subsets(list(range(1,10000)))
"""
(a) (5.0 points)
Complete the following implementation of count_subsets.
def count_subsets(s):
def helper(sum_so_far, index):
if ___(a)___:
if ___(b)___:
return 1
return 0
return ___(c)___ + ___(d)___
return helper(0,0)
i. (1.0 pt) Fill in blank (a).
# index == s
index == len(s)
# sum_so_far == 100
# sum_so_far != 100
ii. (1.0 pt) Fill in blank (b).
# index == s
# index == len(s)
sum_so_far == 100
# sum_so_far != 100
iii. (1.0 pt) Fill in blank (c).
# count_subsets(s[index:])
# count_subsets(s[1:])
# helper(sum_so_far, index)
helper(sum_so_far, index + 1)
iv. (2.0 pt) Fill in blank (d).
helper(sum_so_far+s[index], index + 1)

## Page 13

(b) (2.0 points)
i. (1.0 pt) What is the order of growth of the time required to evaluate count_subsets, in terms of the
length of s?
Exponential
# Quadratic
# Linear
# Logarithmic
# Constant
ii. (1.0 pt) We decide to rewrite count_subsets, following a different approach:
def count_subsets(s):
values = [1]+[0]*100
for i in s:
for j in reversed(range(100-i+1)):
values[j+i]+=values[j]
return values[100]
What is the order of growth of the time required to evaluate the new version of count_subsets, in
terms of the length of s?
# Exponential
# Quadratic
Linear
# Logarithmic
# Constant


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](../61a-fa22-final/p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](../61a-fa22-final/p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](../61a-fa22-final/p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](../61a-fa22-final/p04-advent-of-code.md)
- [61a-fa22-final / P05-TWO-CENTS](../61a-fa22-final/p05-two-cents.md)
- [61a-fa22-final / P06-BARKING-UP-THE-WRONG-TREE](../61a-fa22-final/p06-barking-up-the-wrong-tree.md)
- [61a-fa22-final / P07-ONE-CENT](../61a-fa22-final/p07-one-cent.md)
- [61a-fa22-final / P08-A-PARENTHESES-SCHEME](../61a-fa22-final/p08-a-parentheses-scheme.md)
- [61a-fa22-final / P09-POKEMON-SQARLET](../61a-fa22-final/p09-pokemon-sqarlet.md)
- [61a-fa22-final / P13-OPTIONAL](../61a-fa22-final/p13-optional.md)
- [61a-fa22-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa22-mt1/p01-what-would-python-display.md)
- [61a-fa22-mt1 / P02-DON-T-CALL-ME-I-LL-CALL-YOU](../61a-fa22-mt1/p02-don-t-call-me-i-ll-call-you.md)
- [61a-fa22-mt1 / P03-IT-S-PERFECT](../61a-fa22-mt1/p03-it-s-perfect.md)
- [61a-fa22-mt1 / P04-SUPER-POWERS](../61a-fa22-mt1/p04-super-powers.md)
- [61a-fa22-mt1 / P05-A-QUESTION-1-BUSY-BEAVER](../61a-fa22-mt1/p05-a-question-1-busy-beaver.md)
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](p08-optional.md)
