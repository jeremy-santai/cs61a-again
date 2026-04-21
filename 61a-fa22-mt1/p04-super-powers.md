---
course: CS61A
term: Fall 2022
assessment: MT1
exam_slug: 61a-fa22-mt1
problem_number: 4
problem_title: "Super Powers"
topics: ["higher-order-functions"]
---

# Problem 4 — Super Powers

## Full Extracted Content
## Page 10

4. (4.0 points)
Super Powers
Definition. A function power, written f n(x), describes repeated application of a function f to x. f 2(x) = f(f(x)),
f 5(x) = f(f(f(f(f(x))))), and so on.
(a) (2.0 pt) Choose all correct implementations of funsquare, a function that takes a one-argument function f. It
returns a one-argument function f2 such that f2(x) has the same behavior as f(f(x)) for all x.
>>> triple = lambda x: 3 * x
>>> funsquare(triple)(5)
# Equivalent to triple(triple(5))
A:
def funsquare(f):
D:
def funsquare(f):
return f(f)
return lambda x: f(f(x))
B:
def funsquare(f):
E:
def funsquare(f, x):
return lambda: f(f)
return f(f(x))
C:
def funsquare(f, x):
F:
def funsquare(f):
def g(x):
def g(x):
return f(f(x))
return f(f(x))
return g
return g
2 A
2 B
2 C
■D
2 E
■F
C and E receive two inputs, while funsquare is defined to only receive one input; thus, these two are incorrect.
For A and B, we end up calling f with a function as an argument, even if f expects to receive an integer as an
argument. Thus, these two cannot work.
D and F both work; we can verify this by trying to run these functions on the doctests.
(b) (1.0 pt) Fill in the blank to assign quadruple to a function that takes a number x and returns 4x.
>>> quadruple = funsquare(__<BLANK 1>__)
>>> quadruple(3)
# 4 * 3
BLANK 1
lambda x: 2 * x
quadruple is the result of doubling a number twice, so we should fill blank 1 with a lambda function that doubles
its input.

## Page 11

(c) (1.0 pt) Fill in the blank to assign funfourth to a function that takes a one-argument function f(x) and returns
a one-argument function f 4(x). You may not use a lambda expression.
>>> funfourth = __<BLANK 2>__
>>> funfourth(triple)(10)
# 10 * 3 * 3 * 3 * 3 (triple is defined near the top of the page)
BLANK 2
funsquare(funsquare)
f 4(x) is f(f(f(f(x)))), which is also f 2(f 2(x)). To apply f 2 twice, we call funsquare(funsquare), which returns
a function that takes f and calls funsquare(funsquare(f)).


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
- [61a-fa22-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa22-mt1 / P02-DON-T-CALL-ME-I-LL-CALL-YOU](p02-don-t-call-me-i-ll-call-you.md)
- [61a-fa22-mt1 / P03-IT-S-PERFECT](p03-it-s-perfect.md)
- [61a-fa22-mt1 / P05-A-QUESTION-1-BUSY-BEAVER](p05-a-question-1-busy-beaver.md)
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](../61a-fa22-mt2/p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](../61a-fa22-mt2/p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](../61a-fa22-mt2/p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](../61a-fa22-mt2/p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](../61a-fa22-mt2/p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](../61a-fa22-mt2/p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](../61a-fa22-mt2/p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](../61a-fa22-mt2/p08-optional.md)
