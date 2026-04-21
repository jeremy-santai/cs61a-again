---
course: CS61A
term: Fall 2022
assessment: MT2
exam_slug: 61a-fa22-mt2
problem_number: 7
problem_title: "A+ Question 2: Deforestation"
topics: ["higher-order-functions", "trees"]
---

# Problem 7 — A+ Question 2: Deforestation

## Full Extracted Content
## Page 17

7. (0.0 points)
A+ Question 2: Deforestation
This A+ question is not worth any points. It can only affect your course grade if you have a high
A and might receive an A+. Finish the rest of the exam first!
Implement the function tree_to_graph, which takes as input a Tree instance. It returns a Graph instance
(defined in the previous question) corresponding to the tree, with nodes ordered in pre-order starting with 0.
Pre-order is defined as:
• The root node is assigned the lowest value unassigned.
• After this, the first branch of the tree is assigned values according to pre-order.
• Then, the second branch of the tree is assigned values, and so on.
For example, calling tree_to_graph on this Tree instance to the left should create this Graph instance to the
right.
def tree_to_graph(tree):
def helper(tree, op1, op2):
a = op1()
return op2(a, [helper(b, op1, op2) for b in tree.branches]) or a
num_nodes = helper(tree, ___(a)___, ___(b)___)
g = Graph(num_nodes)
b = iter(range(num_nodes))
helper(tree, ___(c)___,___(d)___)
return g
(a) (0.0 pt) Fill in blank (a).
lambda: 1
(b) (0.0 pt) Fill in blank (b).
lambda a, b: a+sum(b)
(c) (0.0 pt) Fill in blank (c).
lambda: next(b)

## Page 18

(d) (0.0 pt) Fill in blank (d).
lambda a, b: any([g.add_edge(a,i) for i in b])
See the following page for an explanation.


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
- [61a-fa22-mt2 / P08-OPTIONAL](p08-optional.md)
