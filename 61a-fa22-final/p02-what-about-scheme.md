---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 2
problem_title: "What About Scheme?"
topics: ["scheme"]
---

# Problem 2 — What About Scheme?

## Full Extracted Content
## Page 7

2. (4.0 points)
What About Scheme?
Choose the output displayed by the interactive Scheme interpreter when each expression below is
evaluated.
To help distinguish between the backtick (`) and apostrophe (') characters: The first character in subpart 3’s
line of code is a backtick. All remaining ticks are apostrophes (the first character of line 2, the 8th non-space
character of line 3, and three characters in line 4).
(a) (1.0 pt) (+ (* 3 2) (+ 3 2))
# (+ (* 3 2) (+ 3 2))
# (+ 6 (+ 3 2))
# (+ (* 3 2) 5)
# (+ 6 5)
(b) (1.0 pt) '(+ (* 3 2) (+ 3 2))
# 11
(+ (* 3 2) (+ 3 2))
# (+ 6 (+ 3 2))
# (+ (* 3 2) 5)
# (+ 6 5)
(c) (1.0 pt) ` (+ ,(* 3 '2) (+ 3 2))
# 11
# (+ (* 3 2) (+ 3 2))
(+ 6 (+ 3 2))
# (+ (* 3 2) 5)
# (+ 6 5)
# Error
(d) (1.0 pt) '(+ (* '3 2) '(+ 3 2))
# 11
# (+ (* 3 2) (+ 3 2))
# (+ (* 3 2) (quote (+ 3 2)))
# (+ (* (quote 3) 2) (+ 3 2))
(+ (* (quote 3) 2) (quote (+ 3 2)))
# (+ (* 3 2) (quasiquote (+ 3 2)))
# (+ (* (quasiquote 3) 2) (+ 3 2))
# (+ (* (quasiquote 3) 2) (quasiquote (+ 3 2)))
# Error


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](p01-what-would-python-do.md)
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
