---
        course: CS61A
        term: Fall 2021
        assessment: MT2
        source_pdf: 61a-fa21-mt2_sol.pdf
        exam_slug: 61a-fa21-mt2
        problem_number: 5
        problem_title: "Groot"
        page_range: [14, 16]
        topics: ["linked-lists", "lists", "trees", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 5 — Groot

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: MT2
        - Source PDF: `61a-fa21-mt2_sol.pdf`
        - Pages: 14-16

        ## Full extracted content

        ## Page 14

5. (9.0 points)
Groot
Definition. A twig is a tree that is not a leaf but whose branches are all leaves.
The Tree and Link classes appear on your midterm 2 study guide. Assume they are defined.
(a) (4.0 points)
Implement twig, which takes a Tree instance t. It returns True if t is a twig and False otherwise.
def twig(t):
"""Return True if Tree t is a twig and False otherwise.
>>> twig(Tree(1))
False
>>> twig(Tree(1, [Tree(2), Tree(3)]))
True
>>> twig(Tree(1, [Tree(2), Tree(3, [Tree(4)])]))
False
"""
return _________ and _________
(a)
(b)
i. (2.0 pt) Which of these could fill in blank (a)? Check all that apply. Hint: The bool function returns
True for a true value and False for a false value.
2 t
2 bool(t)
2 t.is_leaf()
■not t.is_leaf()
2 t.branches
■bool(t.branches)
2 len(t.branches)
■len(t.branches) > 0
2 len(t.branches) >= 0
ii. (2.0 pt) Fill in blank (b).
all([b.is_leaf() for b in t.branches])

## Page 15

(b) (5.0 points)
Implement twigs, which takes a Tree instance t. It returns a linked list (either a Link instance or
Link.empty) containing all of the labels of the twigs in t. Labels should be in the same order as they
appear in repr(t).
def twigs(t):
"""Return a linked list of the labels of the twigs in t.
>>> t = Tree(1, [Tree(2), Tree(3, [Tree(4)]), Tree(5, [Tree(6, [Tree(7), Tree(8)])])])
>>> print(twigs(t))
<3 6>
>>> print(twigs(Tree(0, [t, t, t])))
<3 6 3 6 3 6>
>>> twigs(Tree(0)) is Link.empty
True
"""
def add_twigs(t, rest):
if twig(t):
return _________
(a)
for b in reversed(t.branches):
rest = _________
(b)
return rest
return add_twigs(t, _________)
(c)
i. (2.0 pt) Fill in blank (a).
Link(t.label, rest)
ii. (2.0 pt) Fill in blank (b).
add_twigs(b, rest)
iii. (1.0 pt) Fill in blank (c).
Link.empty

## Page 16

No more questions.


---

## Same Semester

- [61a-fa21-final / P01-HOUSE-ATREIDES](../61a-fa21-final/p01-house-atreides.md)
- [61a-fa21-final / P02-ARRAKIS](../61a-fa21-final/p02-arrakis.md)
- [61a-fa21-final / P03-CALADAN](../61a-fa21-final/p03-caladan.md)
- [61a-fa21-final / P04-SPICE](../61a-fa21-final/p04-spice.md)
- [61a-fa21-final / P05-GOM-JABBAR](../61a-fa21-final/p05-gom-jabbar.md)
- [61a-fa21-final / P06-JUST-FOR-FUN](../61a-fa21-final/p06-just-for-fun.md)
- [61a-fa21-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa21-mt1/p01-what-would-python-display.md)
- [61a-fa21-mt1 / P02-31-CAL-OLYMPIANS](../61a-fa21-mt1/p02-31-cal-olympians.md)
- [61a-fa21-mt1 / P03-ALL-HAIL-THE-STONE](../61a-fa21-mt1/p03-all-hail-the-stone.md)
- [61a-fa21-mt2 / P01-HAWKEYE](p01-hawkeye.md)
- [61a-fa21-mt2 / P02-DOCTOR-CHANGE](p02-doctor-change.md)
- [61a-fa21-mt2 / P03-SHANG-CHI](p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](p04-thanos.md)
