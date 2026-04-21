---
course: CS61A
term: Fall 2022
assessment: MT1
exam_slug: 61a-fa22-mt1
problem_number: 2
problem_title: "Don’t Call Me, I’ll Call You"
topics: ["environment-diagrams", "higher-order-functions"]
---

# Problem 2 — Don’t Call Me, I’ll Call You

## Full Extracted Content
## Page 4

2. (12.0 points)
Don’t Call Me, I’ll Call You
When working on a large project, you get the error 'int' object is not callable in the code below during the
second call to f. Complete the environment diagram until the error occurs to identify the problem with the code. If a
blank contains an arrow to a function, write the function as it would appear in the diagram.
Global frame
f1: ___________ [parent=____________]
Return Value
f2: ___________ [parent=____________]
Return Value
f3: ___________ [parent=____________]
Return Value
max
func zero(t) [parent=      ]
f
Global
x
zero
t
z
f4: ___________ [parent=____________]
(h)
1: def f(x):
2:     """f(x)(t) returns max(x*x, 3*x)
3:     if t(x) > 0, and 0 otherwise.
4:     """
5:     y = max(x * x, 3 * x)
6:     def zero(t):
7:
if t(x) > 0:
8:
return y
9:
return 0
10:     return zero
11:
12: # Find the largest positive y below 10
13: # for which f(y)(lambda z: z - y + 10)
14: # is not 0.
15: y = 1
16: while y < 10:
17:     if f(y)(lambda z: z - y + 10):
18:
max = y
19:     y = y + 1
f
y
(a)
(b)
func f(x) [parent=Global]
(c)
y
zero
(d)
(e)
(f)
(g)
λ <line 17>
(i)
... stop here ...
f
Global
x
(a) (1.0 pt) Fill in blank (a).
(b) (1.0 pt) Fill in blank (b).
(c) (1.0 pt) Which of these could fill in blank (c)?
# Global
# f
f1

## Page 5

(d) (1.0 pt) Which of these could fill in blank (d)?
# Global
# f
f1
(e) (2.0 pt) Fill in blank (e).
func λ(z) <line 17> [parent=Global]
(f) (1.0 pt) Fill in blank (f).
(g) (1.0 pt) Which of these could fill in blank (g)?
Global
# f
# zero
# f1
# f2
(h) (1.0 pt) Fill in blank (h).
(i) (1.0 pt) Fill in blank (i).
(j) (2.0 pt) Explain in 10 words or less why the 'int' object is not callable error occurred.
Example answer: “Global max was reassigned to an integer”
The first iteration of the while loop works as intended; f(y) returns the function zero with x set to 1 and y set to
3. We then call zero on lambda z: z - y + 10. This evaluates (lambda z: z - y + 10)(1) == 1 - 1 + 10
== 10. Since 10 > 0, we return y, which is equal to 3. This is truthy, so we set max to 1.
On the second iteration of the loop, we run until line 5. At this point, we evaluate a call expression with max as the
operator. However, max was set to 1 in the previous iteration, overwriting its original assignment to the built-in
max function. Thus, Python tries to call 1 as a function; since 1 is not a function, Python errors, stating that
'int' object is not callable.


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
