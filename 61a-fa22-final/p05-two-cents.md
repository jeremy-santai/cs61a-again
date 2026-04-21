---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 5
problem_title: "Two Cents"
topics: ["cs61a"]
---

# Problem 5 — Two Cents

## Full Extracted Content
## Page 12

5. (5.0 points)
Two Cents
One of the most useful aspects of programming is that code can often be reused to solve similar problems. The
count_change function takes an integer amount of cents and returns the number of ways to make change for
that amount in US currency.
coins = (1, 5, 10, 25, 50)
def count_change(amount):
'''Return the number of ways to make change for amount.
>>> count_change(10) # 10, 5-5, 5-1-1-1-1-1, 1-1-1-1-1-1-1-1-1-1
>>> count_change(20) # 10-10, 10-5-5, 10-5-1-1-1-1-1, 10-1-1-1-1-1-1-1-1-1-1, 5-5-5-5, ...
>>> count_change(100)
'''
def helper(remaining, coin_index):
if coin_index == len(coins) or remaining < 0:
return 0
if remaining == 0:
return 1
return (helper(remaining - coins[coin_index], coin_index
) +
helper(remaining
, coin_index + 1))
return helper(amount, 0)
Modify this code to solve the following new problem:
Your cash register only has k of each type of coin. Implement count_change_register, which counts the
number of ways to make change for amount using at most k coins of each type.
def count_change_register(amount, k):
'''Return the number of ways to make change for amount using at most k of each coin type.
>>> count_change_register(20, 10) # Excludes 20 pennies and excludes 1 nickel + 15 pennies
>>> count_change_register(20, 2) # 10-10, 10-5-5
>>> count_change_register(100, 10)
>>> count_change_register(100, 100)
'''
def helper(remaining, coin_index, n):
if coin_index == len(coins) or remaining < 0 or __(a)__:
return 0
if remaining == 0:
return 1
return (helper(remaining - coins[coin_index], coin_index
, __(b)__ ) +
helper(remaining
, coin_index + 1, __(c)__ ))
return helper(amount, 0, 0)

## Page 13

(a) (2.0 pt) Fill in Blank (a)
# True
# False
# n > 0
# k > 0
n > k
# n == k
# n > 10
# n == 10
(b) (1.0 pt) Fill in Blank (b)
# k
# k - 1
# k + 1
# n
n + 1
# n - 1
# 0
# 10
(c) (1.0 pt) Fill in Blank (c)
# k
# k - 1
# k + 1
# n
# n + 1
# n - 1
# 10
(d) (1.0 pt) What does count_change_register(25, 2) return?
# 0
# 1
# 3
# 4
# None of these


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](p04-advent-of-code.md)
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
