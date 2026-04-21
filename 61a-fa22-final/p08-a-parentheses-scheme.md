---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 8
problem_title: "A Parentheses Scheme"
topics: ["lists", "scheme"]
---

# Problem 8 — A Parentheses Scheme

## Full Extracted Content
## Page 19

8. (6.0 points)
A Parentheses Scheme
In a fit of Scheme-induced rage, you’ve decided that all internal parentheses must be eliminated! Implement the
procedure remove-parens that takes as input a Scheme list and returns that list with all internal parentheses
removed.
;;; > (remove-parens '(((1) 2 3) 4 5 (6 (7)) (8 10)))
;;; (1 2 3 4 5 6 7 8 10)
;;; > (remove-parens '(((a) b (c) ()) (d) e (f (((g)))) (h i)))
;;; (a b c d e f g h i)
(define (remove-parens s)
(cond
( (null? s) nil
)
( __(a)__
__(b)__)
( else
__(c)__)))
(a) (1.0 pt) Fill in Blank (a)
# (list? s)
(list? (car s))
# (list? (cdr s))
# (null? (cdr s))
# (not (number? (car s)))
(b) (3.0 pt) Fill in Blank (b)
(append (remove-parens (car s)) (remove-parens (cdr s)))
(c) (2.0 pt) Select all of the expressions below that could fill in Blank (c).
2 (remove-parens (cdr s))
2 (remove-parens (cons (car s) (cdr s)))
2 (remove-parens (list (car s) (cdr s)))
■(cons (car s) (remove-parens (cdr s)))
2 (cons (remove-parens (car s)) (remove-parens (cdr s)))
2 (list (car s) (remove-parens (cdr s)))
2 (list (remove-parens (car s)) (remove-parens (cdr s)))


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](p04-advent-of-code.md)
- [61a-fa22-final / P05-TWO-CENTS](p05-two-cents.md)
- [61a-fa22-final / P06-BARKING-UP-THE-WRONG-TREE](p06-barking-up-the-wrong-tree.md)
- [61a-fa22-final / P07-ONE-CENT](p07-one-cent.md)
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
