---
        course: CS61A
        term: Fall 2021
        assessment: MT1
        source_pdf: 61a-fa21-mt1_sol.pdf
        exam_slug: 61a-fa21-mt1
        problem_number: 1
        problem_title: "What Would Python Display?"
        page_range: [3, 4]
        topics: ["combinatorics"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 1 — What Would Python Display?

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: MT1
        - Source PDF: `61a-fa21-mt1_sol.pdf`
        - Pages: 3-4

        ## Full extracted content

        ## Page 3

1. (8.0 points)
What Would Python Display?
(a) (4.0 points)
Assume the following code has been executed.
def os(ki):
t = -1
i = 5
t = 7
while i > 3:
t = i - 4 and i + 4
os(i - 2)
i, j = i - 1, i * 2
s = i
i. (1.0 pt) What value is bound to i in the global frame?
ii. (1.0 pt) What value is bound to j in the global frame?
iii. (1.0 pt) What value is bound to s in the global frame?
iv. (1.0 pt) What value is bound to t in the global frame?

## Page 4

(b) (4.0 points)
The function tik takes an argument tok and returns a function insta that takes an argument gram. The
insta function prints tok and gram on the same line separated by a space and has no return statement.
Its implementation has been omitted intentionally.
def tik(tok):
"""Returns a function that takes gram and prints tok and gram on a line.
>>> tik(5)(6)
5 6
"""
def insta(gram):
... # The implementation of this function has been omitted.
return insta
i. (4.0 pt) What would the interactive Python interpreter display upon evaluating the expression:
tik(tik(5)(print(6)))(print(7))
5 None
None None


---

## Same Semester

- [61a-fa21-final / P01-HOUSE-ATREIDES](../61a-fa21-final/p01-house-atreides.md)
- [61a-fa21-final / P02-ARRAKIS](../61a-fa21-final/p02-arrakis.md)
- [61a-fa21-final / P03-CALADAN](../61a-fa21-final/p03-caladan.md)
- [61a-fa21-final / P04-SPICE](../61a-fa21-final/p04-spice.md)
- [61a-fa21-final / P05-GOM-JABBAR](../61a-fa21-final/p05-gom-jabbar.md)
- [61a-fa21-final / P06-JUST-FOR-FUN](../61a-fa21-final/p06-just-for-fun.md)
- [61a-fa21-mt1 / P02-31-CAL-OLYMPIANS](p02-31-cal-olympians.md)
- [61a-fa21-mt1 / P03-ALL-HAIL-THE-STONE](p03-all-hail-the-stone.md)
- [61a-fa21-mt2 / P01-HAWKEYE](../61a-fa21-mt2/p01-hawkeye.md)
- [61a-fa21-mt2 / P02-DOCTOR-CHANGE](../61a-fa21-mt2/p02-doctor-change.md)
- [61a-fa21-mt2 / P03-SHANG-CHI](../61a-fa21-mt2/p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](../61a-fa21-mt2/p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](../61a-fa21-mt2/p05-groot.md)
