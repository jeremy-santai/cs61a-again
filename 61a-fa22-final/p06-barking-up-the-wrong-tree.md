---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 6
problem_title: "Barking up the Wrong Tree"
topics: ["lists", "trees", "oop", "sql"]
---

# Problem 6 — Barking up the Wrong Tree

## Full Extracted Content
## Page 14

6. (6.0 points)
Barking up the Wrong Tree
After years of using SQL, John the Dog Breeder decides to switch to a Python Tree to track his dogs’ heredity.
Implement tree_to_table, which takes a Tree instance t representing dogs. Each node in the tree has a label
that is the name of a dog and children corresponding to the children of that dog. The tree_to_table function
returns a list of the parent-child relationships in t in any order. Each parent-child relationship is represented
as a two-element tuple, where the first element is the name of the parent, and the second is the name of the
child.
The Tree class is defined on page 2 of the Midterm 2 Study Guide with instance attributes label and branches.
You may not use any functions from the study guide defined outside of the Tree class.
For Tree('E', [Tree('F', [Tree('A', [Tree('B'), Tree('C')]), Tree('D', [Tree('H')]), Tree('G')])])
One valid output is:
[('A', 'B'), ('A', 'C'), ('D', 'H'), ('F', 'A'), ('F', 'D'), ('F', 'G'),
('E', 'F')]
def tree_to_table(t):
relationships = __(a)__
for i in __(b)__:
relationships.__(c)__(__(d)__)
return relationships
(a) (3.0 pt) Fill in Blank (a)
[(t.label, i.label) for i in t.branches]
(b) (1.0 pt) Fill in Blank (b)
# branches
t.branches
# Tree.branches
# tree_to_table(branches)
# tree_to_table(t.branches)
# tree_to_table(Tree.branches)
# relationships
# [p for p, c in relationships]
(c) (1.0 pt) Fill in Blank (c)
# append
extend

## Page 15

(d) (1.0 pt) Fill in Blank (d)
# i
# i.branches
# t.branches
tree_to_table(i)
# tree_to_table(i.branches)
# tree_to_table(t.branches)


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](p04-advent-of-code.md)
- [61a-fa22-final / P05-TWO-CENTS](p05-two-cents.md)
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
