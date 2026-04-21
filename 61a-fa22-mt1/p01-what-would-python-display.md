---
course: CS61A
term: Fall 2022
assessment: MT1
exam_slug: 61a-fa22-mt1
problem_number: 1
problem_title: "What Would Python Display?"
topics: ["higher-order-functions"]
---

# Problem 1 — What Would Python Display?

## Full Extracted Content
## Page 2

1. (4.0 points)
What Would Python Display?
Assume the following code has been executed.
bear = -1
oski = lambda print: print(bear)
bear = -2
s = "Knock"
For each expression below, write the output displayed by the interactive Python interpreter when the expression
is evaluated. The output may have multiple lines. If an error occurs, write “Error”, but include all output displayed
before the error. If evaluation would run forever, write “Forever”. To display a function value, write “Function”. The
interactive interpreter displays the value of a successfully evaluated expression, unless it is None.
(a) (1.0 pt) (3 and 4) - 5
# -2
-1
# 1
# 2
# Error
The and operator returns the first falsey value (a false value, but not necessarily False), or the last value if none
are falsey. Since 3 is truthy (a true value, even though it’s not True), 3 and 4 evaluates to 4. 4 - 5 evaluates to
-1.
(b) (1.0 pt) oski(abs)
# -2
# -1
# 1
# Function
# Error
The lambda function bound to oski takes a function and calls it on bear. Thus, oski(abs) evaluates abs(bear).
Since bear isn’t defined in the lambda function, we take the global value of bear, which is -2. abs(-2) is 2.

## Page 3

(c) (2.0 pt) print(print(print(s, s) or print("Who's There?")), "Who?")
Knock Knock
Who’s There?
None
None Who?
Python evaluation order evaluates the operator expression (to a function), then the operands from left to right (to
the arguments), then calls the function on its arguments.
Below, we substitue operands with argument values and describe the side effects of doing so.
print(print(print(s, s) or print("Who’s There?")), "Who?")
print(print(None or print("Who’s There?")), "Who?") ; Calls print on "Knock Knock"
print(print(print("Who’s There?")), "Who?") ; Since None is a false value, None or print(...) evaluates
the print call.
print(print(None), "Who?") ; Calls print on "Who’s There?"
print(None, "Who?") ; Calls print on None
None ; Calls print on two arguments and displays "None Who?"
Since the value of the whole expression is None, that final None is not displayed.


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
- [61a-fa22-mt1 / P02-DON-T-CALL-ME-I-LL-CALL-YOU](p02-don-t-call-me-i-ll-call-you.md)
- [61a-fa22-mt1 / P03-IT-S-PERFECT](p03-it-s-perfect.md)
- [61a-fa22-mt1 / P04-SUPER-POWERS](p04-super-powers.md)
- [61a-fa22-mt1 / P05-A-QUESTION-1-BUSY-BEAVER](p05-a-question-1-busy-beaver.md)
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](../61a-fa22-mt2/p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](../61a-fa22-mt2/p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](../61a-fa22-mt2/p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](../61a-fa22-mt2/p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](../61a-fa22-mt2/p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](../61a-fa22-mt2/p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](../61a-fa22-mt2/p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](../61a-fa22-mt2/p08-optional.md)
