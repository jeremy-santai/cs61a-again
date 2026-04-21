---
course: CS61A
term: Fall 2022
assessment: MT1
exam_slug: 61a-fa22-mt1
problem_number: 5
problem_title: "A+ Question 1: Busy Beaver"
topics: ["higher-order-functions", "lists"]
---

# Problem 5 — A+ Question 1: Busy Beaver

## Full Extracted Content
## Page 12

5. (0.0 points)
A+ Question 1: Busy Beaver
This A+ question is not worth any points. It can only affect your course grade if you have a high A and
might receive an A+. Finish the rest of the exam first!
To receive an A+ in CS 61A, you need at least 300 points in the course overall and must solve 2 A+ questions. To
receive credit for this A+ question, you must answer all parts of it entirely correctly.
Introduced by Tibor Radó in 1962, the Busy Beaver Game aims to find the terminating program of a given length that
produces the most possible output. Here, we’ll explore one approach to generating a lot of output.
Implement b, which takes a zero-argument function f that returns None. The b function calls its argument f 64 times
and returns None.
• You may not use any numbers or strings or any expressions that evaluate to numbers or strings.
• You may not import any functions, but may use built-in functions that do not need to be imported.
• You may not use lists, tuples, or dictionaries.
• Your answer for blank 2 must be no longer than 50 characters, ignoring whitespace.
def b(f):
"""Evaluate f() 64 times.
>>> a = lambda: print('A', end='')
>>> b(a)
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
"""
(lambda g: g(g(g(g(g(g(__<BLANK 1>__)))))))(__<BLANK 2>__)__<BLANK 3>__
(a) (0.0 pt) BLANK 1
f
# g
# f()
# g()
(b) (0.0 pt) BLANK 2 (Your answer must not be longer than 50 characters, ignoring whitespace.)
lambda f: lambda: f() or f()

## Page 13

(c) (0.0 pt) BLANK 3
()
# (f)
# (g)
To solve this, we note that 64 = 26, and that there are exactly 6 gs in the lambda. Thus, our strategy to call f 64
times is as follows:
• Blank 2 should be a function that receives as input a function h and returns a new function that calls h twice.
Since f is guaranteed to return None, we can use h() or h() to call h twice (and return None).
• The first lambda will take in Blank 2 as input g, and run g6 on some input. Since each layer of Blank 2 doubles
the number of function calls, g6 will call its input function 26 = 64 times. This suggests that we should set
Blank 1 to f.
• Therefore, (lambda g: g(g(g(g(g(g(__<BLANK 1>__)))))))(__<BLANK 2>__) creates a function that calls
f() 64 times. We still need to call it, so Blank 3 should call the newly created function. This can be done by
setting Blank 3 to ().


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
- [61a-fa22-mt1 / P04-SUPER-POWERS](p04-super-powers.md)
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](../61a-fa22-mt2/p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](../61a-fa22-mt2/p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](../61a-fa22-mt2/p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](../61a-fa22-mt2/p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](../61a-fa22-mt2/p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](../61a-fa22-mt2/p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](../61a-fa22-mt2/p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](../61a-fa22-mt2/p08-optional.md)
