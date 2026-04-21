---
course: CS61A
term: Fall 2022
assessment: MT2
exam_slug: 61a-fa22-mt2
problem_number: 8
problem_title: "OPTIONAL"
topics: ["higher-order-functions", "trees"]
---

# Problem 8 — OPTIONAL

## Full Extracted Content
## Page 19

8. (0.0 points)
OPTIONAL
(a) (0.0 pt) Draw a picture related to CS 61A or write a program about CS 61A.
A+ question explanation: There are three parts to this question:
• Determining the number of nodes in the tree (blank a and b)
• Creating a graph with the given number of nodes (blank c)
• Adding the appropriate edges to the graph (blank d and e)
Step 2 can be done fairly easily by calling Graph(numnodes)
For Steps 1 and 3, the tricky part is that the requested behavior must be
achieved solely through the two lambda function inputs of the helper.
Step 1 can be done by using op1 as a lambda that returns 1 and op2 as a
function to add the results of all branches
Step 3 is trickier, but can be done if we make op1 return the ID of the
graph node corresponding to the current tree node. As it turns out, the
pre-order definition perfectly matches assigning IDs in numeric order (using
the traversal order given in the helper function), so we can use the iterator
b to perform this. op2 is then set to run add_edge for each element of the
branches, and return a falsey value so that we output a.
Note that the
solution provides must use any instead of all, in order to return False on
leaves.

## Page 20

No more questions.


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
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](p07-a-question-2-deforestation.md)
