---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 1
problem_title: "What Would Python Do?"
topics: ["higher-order-functions", "oop"]
---

# Problem 1 — What Would Python Do?

## Full Extracted Content
## Page 3

1. (15.0 points)
What Would Python Do?
Assume the code below has been executed.
triple = lambda z: 3 * z
dec = lambda z: z - 1
def alt(f, g):
def h(x):
print(fns[0](fns[1](x)))
fns[0] = fns[1]
fns[1] = fns[0]
return h
fns = [f, g]
return h
class Sub:
fns = [lambda z: str(z) + str(z),
lambda z: 2 * z]
def __init__(self, f, g):
self.fns = [f, g]
def h(self, x):
print(Sub.fns[0](Sub.fns[1](x)))
Sub.fns = self.fns
return self
def __repr__(self):
return str(self.fns[0]('ha'))
class Pub(Sub):
fns = [lambda z: [z],
lambda z: z]
def __init__(self, f, g):
fns = [f, g]
# Careful!
What is the output displayed by the interactive Python interpreter after evaluating each of the following
expressions.
Expressions are evaluated in order, and earlier expressions may affect later ones.
All of the expressions for this question appear here (so that you can work out the answer without flipping pages),
but answer the question using the multiple choice prompts on the following pages.
>>> print(20, (lambda x: print)(20)(22))
>>> (print(4) or 3+2) or 1/0
>>> alt(triple, dec)(8)(8)
>>> Sub(triple, dec).h(8).h(8)
>>> [f(8) for f in Pub(dec, triple).fns]
>>> Pub(dec, triple).h(8).h(8)

## Page 4

(a) (1.0 pt) What is the first line displayed for the first expression: print(20, (lambda x: print)(20)(22))
# 20
# 20 None
# 22 None
# A function value
(b) (1.0 pt) What is the second line displayed for the first expression: print(20, (lambda x: print)(20)(22))
# 20
# 22
20 None
# 22 None
# A function value
(c) (1.0 pt) What is the first line displayed for the second expression: (print(4) or 3+2) or 1/0
# 5
# 4 5
# None 5
# There is no first line because an error occurs
(d) (1.0 pt) What is the second line displayed for the second expression: (print(4) or 3+2) or 1/0
# 4
# 4 5
# None 5
# There is no second line because an error occurs
(e) (1.0 pt) What is the first line displayed for the third expression: alt(triple, dec)(8)(8)
# 6
# 23
# 72
(f) (1.0 pt) What is the second line displayed for the third expression: alt(triple, dec)(8)(8)
# 21
# 23
# 72

## Page 5

(g) (1.0 pt) What is the third line displayed for the third expression: alt(triple, dec)(8)(8)
A function
# None
# 'h'
# h
# There is no third line
(h) (1.0 pt) What is the first line displayed for the fourth expression: Sub(triple, dec).h(8).h(8)
# 8
# 12
# 16
# 21
# '8888'
# There is no first line because an error occurs
(i) (1.0 pt) What is the second line displayed for the fourth expression: Sub(triple, dec).h(8).h(8)
# 8
# 12
# 16
# 1616
# There is no second line because an error occurs
(j) (1.0 pt) What is the third line displayed for the fourth expression: Sub(triple, dec).h(8).h(8)
# A function
# ha
# haha
hahaha
# ['ha']
# ['haha']
# ['hahaha']
# There is no third line (for any reason, including an error)

## Page 6

(k) (2.0 pt) What is displayed for the fifth expression: [f(8) for f in Pub(dec, triple).fns]
# [7, 21]
# [7, [21]]
# ['88', 16]
# ['88', [16]]
[[8], 8]
# [[8], [8]]
# None of these
(l) (1.0 pt) What is the first line displayed for the sixth expression: Pub(dec, triple).h(8).h(8)
# 8
# [8]
# 23
# 1616
# '8888'
(m) (1.0 pt) What is the second line displayed for the sixth expression: Pub(dec, triple).h(8).h(8)
# 8
[8]
# 21
# 23
# 1616
# '8888'
(n) (1.0 pt) What is the third line displayed for the sixth expression: Pub(dec, triple).h(8).h(8)
# A function
# ha
# haha
# hahaha
['ha']
# ['haha']
# ['hahaha']
# There is no third line (for any reason, including an error)


---

## Same Semester

- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](p04-advent-of-code.md)
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
