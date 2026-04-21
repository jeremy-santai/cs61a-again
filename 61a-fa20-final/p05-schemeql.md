---
        course: CS61A
        term: Fall 2020
        assessment: Final
        source_pdf: 61a-fa20-final_sol.pdf
        exam_slug: 61a-fa20-final
        problem_number: 5
        problem_title: "SchemeQL"
        page_range: [23, 26]
        topics: ["higher-order-functions", "lists", "scheme"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 5 — SchemeQL

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: Final
        - Source PDF: `61a-fa20-final_sol.pdf`
        - Pages: 23-26

        ## Full extracted content

        ## Page 23

5. (10.0 points)
SchemeQL
(a) (4.0 points)
Implement the procedure cons that behaves just like the built-in cons when called on a value x and a
(possibly empty) list s. You may not write cons in your solution.
(define (cons x s) ( _________ _________ _________ ))
;
(a)
(b)
(c)
i. (1.0 pt) Which of these could fill in blank (a)?
# list
append
# if
# map
# lambda
ii. (2.0 pt) Fill in blank (b).
(list x)
iii. (1.0 pt) Which of these could fill in blank (c)? Check all that apply.
■s
2 (cdr s)
2 (car s)
2 (list s)

## Page 24

(b) (6.0 points)
The join procedure takes two lists of lists s and t. It returns a list of lists that has one element for each
possible pairing of an element of s with an element of t. Each element of the result is a list that has all
the elements of a list from s followed by all the elements of a list from t.
For example:
scm> (define instructors '(
(john 61a)
(hany 61a)
(josh 61b)))
instructors
scm> (define grades '(
(a b)
(c d)))
grades
scm> (join instructors grades)
((john 61a a b) (john 61a c d) (hany 61a a b) (hany 61a c d) (josh 61b a b) (josh 61b c d))
Implement join.
(define (join s t)
(if (null? s) nil
(_________ (_________ (lambda (v) (_________ _________ _________)) t)
;
(a)
(b)
(c)
(d)
(e)
(join _________ t))))
;
(f)
i. (1.0 pt) Fill in blank (a) with a single procedure name or symbol.
append
ii. (1.0 pt) Fill in blank (b) with a single procedure name or symbol.
map
iii. (1.0 pt) Fill in blank (c) with a single procedure name or symbol.
append
iv. (1.0 pt) Fill in blank (d).
(car s)

## Page 25

v. (1.0 pt) Which of these could fill in blank (e)?
# s
# t
v
vi. (1.0 pt) Fill in blank (f).
(cdr s)

## Page 26

No more questions.


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](p02-stoned.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](p03-college-party.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](p04-last-lecture-ama.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](../61a-fa20-mt1/p01-down-for-the-count.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](../61a-fa20-mt1/p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](../61a-fa20-mt1/p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](../61a-fa20-mt1/p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](../61a-fa20-mt2/p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](../61a-fa20-mt2/p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](../61a-fa20-mt2/p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](../61a-fa20-mt2/p04-fork-it.md)
