---
        course: CS61A
        term: Fall 2020
        assessment: Final
        source_pdf: 61a-fa20-final_sol.pdf
        exam_slug: 61a-fa20-final
        problem_number: 4
        problem_title: "Last Lecture AMA"
        page_range: [15, 22]
        topics: ["higher-order-functions", "lists", "trees", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 4 — Last Lecture AMA

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: Final
        - Source PDF: `61a-fa20-final_sol.pdf`
        - Pages: 15-22

        ## Visual note

This problem includes one or more embedded figures/diagrams on page(s): 15, 18, 21. If an agent needs exact pointer/layout details, it should also consult the source PDF.

## Full extracted content

        ## Page 15

4. (22.0 points)
Last Lecture AMA
Llambda the llama breeder had four original llamas, but now has 12. An arrow from one llama to another
indicates that the first is a parent of the second. For example, Jackie’s parents are Sidney and Finley.
All llamas except the originals have 2 parents, and each has a unique name.
Definition. An offspring tree is a Tree instance with string labels in which each node represents a llama and
the branches of a node represent its (biological) children.
The Tree class appears on the Midterm 2 Study Guide.
Assume originals is a list of offspring trees for the original four.
originals = [Tree('Charlie', ...), Tree('Sidney', ...),

## Page 16

Tree('Finley', ...), Tree('Frankie', ...)]
(a) (6.0 points)
Implement related, which takes two strings a and b that are names, as well as a list of offspring_trees
for the originals. It returns whether a and b are related. That is, they either share a common ancestor or
one is an ancestor of the other.
def related(a, b, offspring_trees):
"""Return whether the llamas named a and b are related.
>>> related('Charlie', 'Max', originals)
# Grandparent
True
>>> related('Jules', 'Jackie', originals)
# Not related, even though they have child
False
>>> related('Max', 'Jules', originals)
# Both descend from Charlie and Frankie
True
>>> related('Max', 'Jess', originals)
# Both descend from Charlie and Finley
True
"""
def family(t):
"""Return a list of the names of all llamas in Tree t."""
result = _________
#
(a)
for b in t.branches:
result._________(_________)
#
(b)
(c)
return result
for s in _________:
#
(d)
if a in s and b in s:
return True
return False
i. (1.0 pt) Which of these could fill in blank (a)?
# []
# [t]
[t.label]
# list(t.branches)
# [b.label for b in t.branches]

## Page 17

ii. (1.0 pt) Which of these could fill in blank (b)?
# append
extend
# pop
# remove
# insert
iii. (2.0 pt) Fill in blank (c).
family(b)
iv. (2.0 pt) Fill in blank (d).
map(family, offspring_trees)

## Page 18

(b) (8.0 points)
This figure is repeated for convenience:
Implement parents, which takes two strings a and b that are names of llamas, as well as a list of
offspring_trees for the originals. It returns whether a and b are both parents of the same child.
def parents(a, b, offspring_trees):
"""Return whether a and b are both parents of the same child.
>>> parents('Jules', 'Jackie', originals)
# Parents of Alex
True
>>> parents('Jules', 'Finley', originals)
# Parents of Jess
True
>>> parents('Jules', 'Jaidyn', originals)
False
>>> parents('Jules', 'Sidney', originals)
False
"""
storage = {}
def traverse(t):
for b in _________:
#
(a)
if _________:
# (b)
storage[b.label] = []
storage[b.label]._________
#
(c)
_________
#
(d)

## Page 19

for t in _________:
#
(e)
traverse(t)
return _________([a in s and b in s for s in storage._________])
#
(f)
(g)
i. (1.0 pt) Which of these could fill in blank (a)?
t.branches
# b.branches
# branches(t)
# branches(b)
ii. (1.0 pt) Fill in blank (b).
b.label not in storage
iii. (2.0 pt) Fill in blank (c).
append(t.label)
iv. (1.0 pt) Fill in blank (d).
traverse(b)
v. (1.0 pt) Which of these could fill in blank (e)?
offspring_trees
# map(traverse, offspring_trees)
# map(list, offspring_trees)
# filter(traverse, offspring_trees)
# filter(list, offspring_trees)
vi. (1.0 pt) Fill in blank (f) with a single function name.
any

## Page 20

vii. (1.0 pt) Which of these could fill in blank (g)?
values()
# keys()
# items()
# copy()

## Page 21

(c) (6.0 points)
Definition. A llama p is multigenerational if it has a child whose other parent is also a parent of p’s
grandchild.
For example:
• Finley has a child Jess whose other parent Jules is also a parent of Alex, which is Finley’s grandchild.
• Frankie has a child Jan whose other parent Finley is also a parent of Jess, which is Frankie’s grandchild.
Hint: In the diagram above, the labels a through e correspond to the five joined tables in the query and
are meant to help you.
Complete a query that selects a one-column table with the name of each multigenerational llama. The
result has two rows: Finley and Frankie.
SELECT a.parent FROM family AS a, family AS b, family AS c, family AS d, family AS e
WHERE _____ AND _____ AND _____ AND _____ AND _____ AND _____;
(u)
(v)
(w)
(x)
(y)
(z)

## Page 22

i. (1.0 pt) Which of these could fill in blank (u)?
a.child = b.parent
# a.parent = b.parent
# a.child = b.child
ii. (1.0 pt) Which of these could fill in blank (v)?
# b.parent = c.parent
b.parent != c.parent
# b.parent = c.child
# b.parent != c.child
iii. (1.0 pt) Which of these could fill in blank (w)?
b.child = c.child
# b.child != c.child
# b.child < c.child
iv. (1.0 pt) Which of these could fill in blank (x)?
a.parent = d.parent
# a.parent = d.child
# a.parent != d.parent
# a.parent != d.child
v. (1.0 pt) Which of these could fill in blank (y)?
c.parent = e.parent
# c.parent = e.child
# c.parent != e.parent
# c.parent != e.child
vi. (1.0 pt) Which of these could fill in blank (z)?
# d.child = e.parent
d.child = e.child
# d.child != e.parent
# d.child != e.child


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](p02-stoned.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](p03-college-party.md)
- [61a-fa20-final / P05-SCHEMEQL](p05-schemeql.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](../61a-fa20-mt1/p01-down-for-the-count.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](../61a-fa20-mt1/p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](../61a-fa20-mt1/p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](../61a-fa20-mt1/p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](../61a-fa20-mt2/p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](../61a-fa20-mt2/p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](../61a-fa20-mt2/p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](../61a-fa20-mt2/p04-fork-it.md)
