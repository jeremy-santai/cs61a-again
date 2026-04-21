---
        course: CS61A
        term: Fall 2020
        assessment: MT2
        source_pdf: 61a-fa20-mt2_sol.pdf
        exam_slug: 61a-fa20-mt2
        problem_number: 4
        problem_title: "Fork It"
        page_range: [13, 20]
        topics: ["lists", "trees"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 4 — Fork It

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: MT2
        - Source PDF: `61a-fa20-mt2_sol.pdf`
        - Pages: 13-20

        ## Visual note

This problem includes one or more embedded figures/diagrams on page(s): 14, 17. If an agent needs exact pointer/layout details, it should also consult the source PDF.

## Full extracted content

        ## Page 13

4. (20.0 points)
Fork It
The tree data abstraction, which is implemented by the constructor tree, selectors branches and label, and
helper functions is_leaf and is_tree appear on Page 2 (left column) of the Midterm 2 Study Guide. You
may call these functions. Do not violate the abstraction barriers of the tree data abstraction.
(a) (4.0 points)
Implement max_path, which takes a tree t whose labels are all positive numbers and returns the largest
sum of the labels along a path from the root of t to one of its leaves.
You may call tree, label, branches, is_leaf, is_tree, and max_path.
def max_path(t):
"""Return the largest sum of labels along any path from the root to a leaf
of tree t, which has positive numbers as labels.
>>> a = tree(1, [tree(2), tree(3), tree(4, [tree(5)])])
>>> max_path(a) # 1 + 4 + 5
>>> b = tree(6, [a, a, a])
>>> max_path(b) # 6 + 1 + 4 + 5
"""
return _________ + max(_________ + _________)
(a)
(b)
(c)
i. (1.0 pt) Which of the following could fill in blank (a)?
# t
label(t)
# [t]
# [label(t)]
# [0]
# sum([b for b in branches(t)])
# sum([label(b) for b in branches(t)])
ii. (1.0 pt) Which of the following could fill in blank (b)?
# t
# label(t)
# [t]
# [label(t)]
[0]
# [label(b) for b in branches(t)]
iii. (2.0 pt) Fill in blank (c). You may not use the word default.
[max_path(b) for b in branches(t)]

## Page 14

(b) (8.0 points)
Definition. A fork is a tree in which exactly one node has more than one child.
Implement is_fork and its helper function slide. The is_fork function takes a tree t and returns True
if t is a fork and False otherwise.
You may call tree, label, branches, is_leaf, is_tree, max_path, is_fork, and slide.
def is_fork(t):
"""Return whether tree t is a fork.
>>> is_fork(tree(1, [tree(2, [tree(3), tree(4), tree(5)])]))
True
>>> is_fork(tree(1, [tree(2, [tree(3)]), tree(4)]))
True
>>> is_fork(tree(1, [tree(2), tree(3), tree(4)]))
True
>>> is_fork(tree(1, [tree(2, [tree(3, [tree(5)]), tree(4, [tree(6)])])]))
True
>>> is_fork(tree(1))
False
>>> is_fork(tree(1, [tree(2, [tree(3)])]))
False

## Page 15

>>> is_fork(tree(1, [tree(2, [tree(3)]), tree(4, [tree(5), tree(6)])]))
False
>>> is_fork(tree(1, [tree(2, [tree(3, [tree(5, [tree(7), tree(8)]), tree(6)]), tree(4)])]))
False
"""
neck = slide(t)
if is_leaf(neck):
_________
(a)
return _________([_________ for b in branches(_________)])
(b)
(c)
(d)
def slide(t):
"""Return the deepest node within tree t whose ancestors all have exactly one child.
Definition: The ancestors of a node include its parent and the parents of all its ancestors.
>>> deepest = slide(tree(1, [tree(2, [tree(3)])]))
>>> label(deepest)
>>> label(slide(tree(1, [tree(2, [tree(3), tree(4)])])))
"""
while _________:
(e)
t = _________
(f)
return t
i. (1.0 pt) Fill in blank (a).
return False
ii. (1.0 pt) Which of the following could fill in blank (b)?
all
# any
# list
# tree
# branches
# label

## Page 16

iii. (2.0 pt) Fill in blank (c).
is_leaf(slide(b))
iv. (1.0 pt) Which of the following could fill in blank (d)?
# t
# tree
neck
# label(t)
# label(tree)
# label(neck)
v. (1.0 pt) Which of the following could fill in blank (e)?
len(branches(t)) == 1
# len(branches(t)) > 1
# len(branches(t)) != 1
# branches(t) == 1
# branches(t) > 1
# branches(t) != 1
vi. (2.0 pt) Fill in blank (f).
branches(t)[0]

## Page 17

(c) (8.0 points)
Definition. A tree t contains a fork u if u is the result of pruning zero or more nodes from t.
Implement max_fork, which takes a tree t whose labels are all positive integers. It returns the largest sum
of the labels of a fork that is contained in t. If t does not contain any forks, then max_fork returns 0.
You may call tree, label, branches, is_leaf, is_tree, max_path, is_fork, slide, and max_fork.
def max_fork(t):
"""Return the largest sum of the labels in any fork contained in tree t,
which has positive numbers as labels. If t contains no forks, return 0.
>>> a = tree(1, [tree(2), tree(3), tree(4, [tree(5)])])
>>> max_fork(a) # 1 + 2 + 3 + 4 + 5
>>> b = tree(6, [a, a, a])
>>> max_fork(b)
#
6 + (1 + 4 + 5) + (1 + 4 + 5) + (1 + 4 + 5)
>>> c = tree(7, [tree(8), b, tree(9)])
>>> max_fork(c)
#
7 + (6 + (1 + 4 + 5) + (1 + 4 + 5) + (1 + 4 + 5))
>>> d = tree(9, [c])
>>> max_fork(d)
# 9 + 7 + (6 + (1 + 4 + 5) + (1 + 4 + 5) + (1 + 4 + 5))
>>> max_fork(tree(1, [tree(2, [tree(3)])])) # No forks here!
"""
n = len(branches(t))
if n == 0:
return 0
elif n == 1:
below = _________
(a)
if _________:
(b)

## Page 18

return _________ + below
(c)
else:
return 0
else:
here = sum([_________ for b in branches(t)])
(d)
there = max([_________ for b in branches(t)])
(e)
return label(t) + max(here, there)
i. (2.0 pt) Fill in blank (a).
max_fork(branches(t)[0])
ii. (1.0 pt) Which of the these could fill in blank (b)?
below > 0
# label(t) > 0
# max_fork(t) > 0
# True
# max_fork(t) > max_path(t)
# is_fork(t)
iii. (1.0 pt) Which of these could fill in blank (c)?
# 1
label(t)
# max_path(t)
# label(slide(t))
# max([label(b) for b in branches(t)])
# label(branches(t)[0])
iv. (2.0 pt) Fill in blank (d).
max_path(b)

## Page 19

v. (2.0 pt) Fill in blank (e).
max_fork(b)

## Page 20

No more questions.


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](../61a-fa20-final/p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](../61a-fa20-final/p02-stoned.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](../61a-fa20-final/p03-college-party.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](../61a-fa20-final/p04-last-lecture-ama.md)
- [61a-fa20-final / P05-SCHEMEQL](../61a-fa20-final/p05-schemeql.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](../61a-fa20-mt1/p01-down-for-the-count.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](../61a-fa20-mt1/p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](../61a-fa20-mt1/p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](../61a-fa20-mt1/p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](p03-sparse-lists.md)
