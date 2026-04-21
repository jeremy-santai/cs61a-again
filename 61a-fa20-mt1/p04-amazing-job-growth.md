---
        course: CS61A
        term: Fall 2020
        assessment: MT1
        source_pdf: 61a-fa20-mt1_sol.pdf
        exam_slug: 61a-fa20-mt1
        problem_number: 4
        problem_title: "Amazing Job Growth"
        page_range: [13, 16]
        topics: ["combinatorics"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 4 — Amazing Job Growth

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: MT1
        - Source PDF: `61a-fa20-mt1_sol.pdf`
        - Pages: 13-16

        ## Full extracted content

        ## Page 13

4. (10.0 points)
Amazing Job Growth
Definition. A repeatable function is a function that returns a repeatable function.
Reminder. You may call built-in functions that do not require import, such as min, max, abs, and pow.
(a) (4.0 points)
Implement growth, which takes a number baseline and returns a repeatable function increase. When
increase is called on a number observed, it prints the difference between observed and the smallest
argument passed to growth or increase so far among the repeated calls.
def growth(baseline):
"""Return a function that can be called repeatedly on numbers and prints
the difference between its argument and the smallest argument used so far
(including baseline).
>>> job = growth(148)(149)(150)(130)(133)(139)(137)
"""
def increase(observed):
under = _________
(a)
print(observed - under)
return _________
(b)
return increase
i. (2.0 pt) Fill in blank (a).
min(observed, baseline)
ii. (2.0 pt) Which of these could fill in blank (b)?
# increase
# increase(under)
# increase(observed)
# increase(baseline)
# growth
growth(under)
# growth(observed)
# growth(baseline)

## Page 14

(b) (6.0 points)
Implement maxer, a higher-order function that takes a function smoke, which takes a number and returns
a number. The maxer function returns a repeatable function fire that takes a number y and prints the
largest result of calling smoke on any value of y passed to fire so far among the repeated calls.
Assume that smoke is a deterministic pure function.
def square(x):
return x * x
def maxer(smoke):
"""Return a repeatable function fire(y) that prints the largest smoke(y) so far.
>>> g = maxer(square)
>>> h = g(2)(1)(3)(2)(-4)
# print the largest square(y) so far
>>> h = maxer(abs)(2)(1)(3)(2)(-4)
# print the largest abs(y) so far
"""
def fire(y):
_________
(a)
def haze(z):
if _________:
(b)
z = y
return _________
(c)
return haze
return fire
i. (2.0 pt) Fill in blank (a). You may not write a return statement for this blank.
print(smoke(y))

## Page 15

ii. (2.0 pt) Fill in blank (b).
smoke(y) > smoke(z)
iii. (2.0 pt) Which of these could fill in blank (c)?
# y
# smoke(y)
# fire(y)
# fire(smoke(y))
# haze
# haze(y)
# haze(smoke(y))
# z
# smoke(z)
fire(z)
# fire(smoke(z))
# haze(z)
# haze(smoke(z))

## Page 16

No more questions.


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](../61a-fa20-final/p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](../61a-fa20-final/p02-stoned.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](../61a-fa20-final/p03-college-party.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](../61a-fa20-final/p04-last-lecture-ama.md)
- [61a-fa20-final / P05-SCHEMEQL](../61a-fa20-final/p05-schemeql.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](p01-down-for-the-count.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](p03-please-register-to-vote.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](../61a-fa20-mt2/p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](../61a-fa20-mt2/p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](../61a-fa20-mt2/p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](../61a-fa20-mt2/p04-fork-it.md)
