---
course: CS61A
term: Fall 2022
assessment: MT2
exam_slug: 61a-fa22-mt2
problem_number: 4
problem_title: "The Lambdanean Hydra"
topics: ["higher-order-functions", "trees"]
---

# Problem 4 — The Lambdanean Hydra

## Full Extracted Content
## Page 9

4. (9.0 points)
The Lambdanean Hydra
Heracles is fighting the Lambdanean Hydra, a many-headed monster, where two heads regrow when one head
gets chopped off. A hydra is represented by a tree, each head is represented by a leaf labeled 1, and each non-leaf
node has two branches and is labeled with the number of leaves among its descendants. Here’s a six-headed
hydra named lerna:
lerna=Tree(6,[Tree(4,[Tree(2,[Tree(1),Tree(1)]),Tree(2,[Tree(1),Tree(1)])]),Tree(2,[Tree(1),Tree(1)])]
(a) (4.0 points)
Implement is_hydra, which takes in as input a Tree instance t and determines if t represents a valid
hydra.
def is_hydra(t):
"""Return True if Tree instance t properly represents a hydra and False otherwise.
>>> is_hydra(Tree(1))
True
>>> is_hydra(Tree(2, [Tree(1), Tree(1)]))
True
>>> is_hydra(Tree(3, [Tree(1), Tree(2)]))
# Wrong leaf label
False
>>> is_hydra(Tree(3, [Tree(1), Tree(1)]))
# Wrong root label
False
>>> is_hydra(Tree(3, [Tree(3, [Tree(1), Tree(1)]), Tree(1)]))
# Wrong node label below root
False
>>>is_hydra(lerna)
# lerna the six-headed hydra is defined above
True
"""
if t.is_leaf():
return t.label == 1
if len(t.branches) != 2:
return False
return (t.label == ___(a)___) and ___(b)___
i. (2.0 pt) Fill in blank (a).
sum([b.label for b in t.branches])
ii. (2.0 pt) Fill in blank (b).
is_hydra(t.branches[0]) and is_hydra(t.branches[1])

## Page 10

(b) (5.0 points)
If Heracles cuts off the second head from the left, two new heads appear there, and all ancestor labels are
updated.
Implement chop_head(hydra, n), which takes as input a Tree instance hydra representing a hydra and a
positive integer n. It mutates hydra by chopping off the nth head from the left (adding two new adjacent
heads in its place).
def chop_head(hydra, n):
"""
>>> lerna = Tree(1)
>>> chop_head(lerna, 1)
# Note that n is 1-indexed
>>> chop_head(lerna, 1)
>>> chop_head(lerna, 3)
>>> chop_head(lerna, 1)
>>> chop_head(lerna, 3)
>>> lerna
# Now lerna is a six-headed hydra (above left)
Tree(6,[Tree(4,[Tree(2,[Tree(1),Tree(1)]),Tree(2,[Tree(1),Tree(1)])]),
Tree(2,[Tree(1),Tree(1)])])
>>> chop_head(lerna, 2)
>>> lerna
# The mutated lerna now has seven heads (above right)
Tree(7,[Tree(5,[Tree(3,[Tree(1),Tree(2,[Tree(1),Tree(1)])]),Tree(2,[Tree(1),Tree(1)])]),
Tree(2,[Tree(1),Tree(1)])])
"""
assert is_hydra(hydra)
assert n > 0 and n <= hydra.label
if hydra.is_leaf():
___(a)___
# This blank may be filled with multiple lines of code
return
___(b)___
left, right = hydra.branches
if ___(c)___:
chop_head(right, ___(d)___)
else:
chop_head(left, n)

## Page 11

i. (2.0 pt) Select all options that could fit in blank (a), which may have multiple lines.
Option 1:
hydra = Tree(2,[Tree(1), Tree(1)])
Option 2:
for _ in range(2):
hydra.branches.append(Tree(1))
hydra.label = 2
Option 3:
hydra.label = Tree(2)
hydra.branches = [Tree(1),Tree(1)]
Option 4:
hydra.label = 2
hydra.branches = [Tree(1), Tree(1)]
Option 5:
hydra.label = 2
hydra.branches = [Tree(1)] * 2
2 Option 1
■Option 2
2 Option 3
■Option 4
2 Option 5
ii. (1.0 pt) Fill in blank (b).
hydra.label += 1
iii. (1.0 pt) Fill in blank (c).
n > left.label
iv. (1.0 pt) Fill in blank (d).
n - left.label


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
- [61a-fa22-mt2 / P05-AIM-FOR-100](p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](p08-optional.md)
