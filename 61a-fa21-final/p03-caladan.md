---
        course: CS61A
        term: Fall 2021
        assessment: Final
        source_pdf: 61a-fa21-final_sol.pdf
        exam_slug: 61a-fa21-final
        problem_number: 3
        problem_title: "Caladan"
        page_range: [16, 17]
        topics: ["trees", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 3 — Caladan

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: Final
        - Source PDF: `61a-fa21-final_sol.pdf`
        - Pages: 16-17

        ## Full extracted content

        ## Page 16

3. (8.0 points)
Caladan
Definition. A fruit is a leaf node that has a parent but no siblings. That is, its parent has no other children.
The Tree class appears on page 2 (left column) of the midterm 2 study guide.
You may use fruited_branch in the problems below.
def fruited_branch(t):
"""Return whether Tree t has exactly one child that is a fruit (a leaf with no siblings).
>>> fruited_branch(Tree(4))
False
>>> fruited_branch(Tree(4, [Tree(5)]))
True
>>> fruited_branch(Tree(4, [Tree(5, [Tree(6)])]))
False
"""
return len(t.branches) == 1 and t.branches[0].is_leaf()
(a) (4.0 points)
Implement sum_fruit_labels, which takes a Tree instance t. It returns the sum of the labels of the fruits
in t. If t has no fruits, 0 is returned.
def sum_fruit_labels(t):
"""Return the sum of the labels of the fruits of Tree t.
>>> apple = Tree(5, [Tree(6, [Tree(7)]), Tree(8), Tree(9, [Tree(10)])])
>>> sum_fruit_labels(apple)
# 7 + 10
>>> pineapple = Tree(3, [Tree(4), apple, apple, Tree(1, [Tree(2)])])
>>> sum_fruit_labels(pineapple)
# 7 + 10 + 7 + 10 + 2
>>> sum_fruit_labels(Tree(3, [Tree(4), Tree(5)]))
# No fruits!
"""
if fruited_branch(t):
return _________
(a)
else:
return _________
(b)
i. (2.0 pt) Fill in blank (a).
t.branches[0].label
ii. (2.0 pt) Fill in blank (b).
sum([sum_fruit_labels(b) for b in t.branches])

## Page 17

(b) (4.0 points)
Implement pruned, which takes a Tree instance t. If t contains at least one fruit, it returns a Tree
instance with only the nodes of t that appear on a path from the root to a fruit. If t contains no fruit,
pruned(t) returns None. Calling pruned(t) should not modify t.
def pruned(t):
"""Return a Tree with only the nodes of t that are on a path to a fruit.
>>> t = Tree(5, [Tree(6, [Tree(7)]), Tree(8), Tree(9, [Tree(10)])])
>>> pruned(t)
Tree(5, [Tree(6, [Tree(7)]), Tree(9, [Tree(10)])])
>>> t
# t is not modified by calling pruned(t)
Tree(5, [Tree(6, [Tree(7)]), Tree(8), Tree(9, [Tree(10)])])
>>> pruned(Tree(2, [Tree(3), Tree(4)])) is None
# No fruit!
True
"""
if fruited_branch(t):
return _________
(a)
cut = [pruned(b) for b in t.branches]
# Some items in cut might be None
if _________:
(b)
return _________
(c)
i. (1.0 pt) Which of these could fill in blank (a)?
t
# t.branches[0]
# Tree(t.label)
# Tree(t.label, t.branches[0])
# Tree(t.label, [b for b in t.branches if fruited_branch(b)])
ii. (1.0 pt) Which of these could fill in blank (b)?
# cut
# cut is not None
# None in cut
any(cut)
# all(cut)
iii. (2.0 pt) Fill in blank (c).
Tree(t.label, [b for b in cut if b])


---

## Same Semester

- [61a-fa21-final / P01-HOUSE-ATREIDES](p01-house-atreides.md)
- [61a-fa21-final / P02-ARRAKIS](p02-arrakis.md)
- [61a-fa21-final / P04-SPICE](p04-spice.md)
- [61a-fa21-final / P05-GOM-JABBAR](p05-gom-jabbar.md)
- [61a-fa21-final / P06-JUST-FOR-FUN](p06-just-for-fun.md)
- [61a-fa21-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa21-mt1/p01-what-would-python-display.md)
- [61a-fa21-mt1 / P02-31-CAL-OLYMPIANS](../61a-fa21-mt1/p02-31-cal-olympians.md)
- [61a-fa21-mt1 / P03-ALL-HAIL-THE-STONE](../61a-fa21-mt1/p03-all-hail-the-stone.md)
- [61a-fa21-mt2 / P01-HAWKEYE](../61a-fa21-mt2/p01-hawkeye.md)
- [61a-fa21-mt2 / P02-DOCTOR-CHANGE](../61a-fa21-mt2/p02-doctor-change.md)
- [61a-fa21-mt2 / P03-SHANG-CHI](../61a-fa21-mt2/p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](../61a-fa21-mt2/p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](../61a-fa21-mt2/p05-groot.md)
