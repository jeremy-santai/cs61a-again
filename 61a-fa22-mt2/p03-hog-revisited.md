---
course: CS61A
term: Fall 2022
assessment: MT2
exam_slug: 61a-fa22-mt2
problem_number: 3
problem_title: "Hog Revisited"
topics: ["generators", "lists"]
---

# Problem 3 — Hog Revisited

## Full Extracted Content
## Page 7

3. (8.0 points)
Hog Revisited
In Project 1, we created a simulator for the game of Hog without using lists or iterators. Let’s revise the
implementation, but instead of representing dice as zero-argument functions, we’ll represent dice as iterators
over outcomes.
(a) (3.0 points)
Implement make_test_dice, which takes a list of outcomes. It returns an infinite iterator that repeatedly
cycles through the outcomes.
def make_test_dice(outcomes):
"""Return an infinite iterator that cycles through the elements of outcomes.
>>> dice = make_test_dice([1, 2, 3])
>>> next(dice)
>>> next(dice)
>>> next(dice)
>>> next(dice)
>>> next(dice)
>>> next(dice)
>>> next(dice)
>>> next(dice)
"""
outcomes = list(outcomes)
while True:
for i in ___(a)___:
___(b)___
i. (1.0 pt) Which of these could fill in blank (a)? Select all that apply.
■outcomes
2 outcomes + make_test_dice(outcomes)
2 outcomes.extend(make_test_dice(outcomes))
2 outcomes[0] + make_test_dice(outcomes[1:])
2 make_test_dice(outcomes) + make_test_dice(outcomes)
2 make_test_dice(outcomes[0]) + make_test_dice(outcomes[1:])
ii. (2.0 pt) Fill in blank (b).
yield i

## Page 8

(b) (5.0 points)
Implement roll_dice, which takes two arguments: a positive integer called num_rolls giving the number
of dice to roll and a dice iterator that provides outcomes. It returns the number of points scored by rolling
the dice num_rolls times in a turn. The points scored are either the sum of the dice outcomes or 1 (Sow
Sad).
• Sow Sad. If any of the dice outcomes is a 1, the current player’s score for the turn is 1.
def roll_dice(num_rolls, dice):
"""Return the number of points scored by rolling dice num_rolls times.
>>> dice = make_test_dice([6, 6, 6, 6, 6, 1])
>>> roll_dice(5, dice) # 6, 6, 6, 6, 6
>>> roll_dice(5, dice) # 1, 6, 6, 6, 6
>>> roll_dice(2, dice) # 6, 1
>>> roll_dice(10,
make_test_dice([2, 4, 3])) # 2, 4, 3, 2, 4, 3, 2, 4, 3, 2
"""
rolls = ___(a)___
if ___(b)___:
return 1
___(c)___
i. (2.0 pt) Fill in blank (a).
[next(dice) for _ in range(num_rolls)]
ii. (1.0 pt) Fill in blank (b).
1 in rolls
iii. (2.0 pt) Fill in blank (c).
return sum(rolls)


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
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](p08-optional.md)
