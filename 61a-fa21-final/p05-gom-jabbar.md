---
        course: CS61A
        term: Fall 2021
        assessment: Final
        source_pdf: 61a-fa21-final_sol.pdf
        exam_slug: 61a-fa21-final
        problem_number: 5
        problem_title: "Gom Jabbar"
        page_range: [22, 22]
        topics: ["environment-diagrams", "scheme", "sql"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 5 — Gom Jabbar

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: Final
        - Source PDF: `61a-fa21-final_sol.pdf`
        - Pages: 22-22

        ## Full extracted content

        ## Page 22

5. (10.0 points)
Gom Jabbar
(a) (4.0 pt) Which of the following strings is entirely matched (from beginning to end) by the regular
expression below? Check all that apply.
(([cs][61]|[abc])?(cs)+)|([cs]+61+)
2 cs61a
2 cs61acscs
■cs61
■cscs
■cscs611
■cccsss61
2 cs6161
■s1cs
(b) (2.0 pt) Write a short string (fewer than 10 characters) that matches the BNF grammar below, but is
guaranteed to cause an error when evaluated by Scheme, regardless of how any symbols such as f are
defined in the environment.
Notes: The %ignore /\s+/ directive ignores whitespace in the string. The INT terminal matches integers.
?start: expr
expr: INT | "(" operator expr+ ")"
operator: PROCEDURE | expr
PROCEDURE: "f"
%ignore /\s+/
%import common.INT
(2 3) or any call expression with an integer literal operator.
(c) (4.0 pt) Write a SQL query that generates a one-column table of the names of all dogs with exactly one
child that has short fur. (The dog may have multiple children, but only one can have short fur.)
Assume the parents and dogs tables from page 1 (right column) of the final study guide have been created.
The result of your query should contain two rows: “Abraham” and “Fillmore”. Your query should select the
rows described even if the contents of parents and dogs were different; no credit for SELECT "Abraham"
UNION SELECT "Fillmore".
SELECT parent FROM parents, dogs WHERE child=name AND fur="short" GROUP
BY parent HAVING COUNT(*)=1;


---

## Same Semester

- [61a-fa21-final / P01-HOUSE-ATREIDES](p01-house-atreides.md)
- [61a-fa21-final / P02-ARRAKIS](p02-arrakis.md)
- [61a-fa21-final / P03-CALADAN](p03-caladan.md)
- [61a-fa21-final / P04-SPICE](p04-spice.md)
- [61a-fa21-final / P06-JUST-FOR-FUN](p06-just-for-fun.md)
- [61a-fa21-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa21-mt1/p01-what-would-python-display.md)
- [61a-fa21-mt1 / P02-31-CAL-OLYMPIANS](../61a-fa21-mt1/p02-31-cal-olympians.md)
- [61a-fa21-mt1 / P03-ALL-HAIL-THE-STONE](../61a-fa21-mt1/p03-all-hail-the-stone.md)
- [61a-fa21-mt2 / P01-HAWKEYE](../61a-fa21-mt2/p01-hawkeye.md)
- [61a-fa21-mt2 / P02-DOCTOR-CHANGE](../61a-fa21-mt2/p02-doctor-change.md)
- [61a-fa21-mt2 / P03-SHANG-CHI](../61a-fa21-mt2/p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](../61a-fa21-mt2/p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](../61a-fa21-mt2/p05-groot.md)
