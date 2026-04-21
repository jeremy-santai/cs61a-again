---
        course: CS61A
        term: Fall 2020
        assessment: MT1
        source_pdf: 61a-fa20-mt1_sol.pdf
        exam_slug: 61a-fa20-mt1
        problem_number: 1
        problem_title: "Down for the Count"
        page_range: [3, 8]
        topics: ["programming-languages"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 1 — Down for the Count

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: MT1
        - Source PDF: `61a-fa20-mt1_sol.pdf`
        - Pages: 3-8

        ## Full extracted content

        ## Page 3

1. (14.0 points)
Down for the Count
Definition. A digit is a non-negative integer less than 10. Integers contain digits.
Examples.
• The integer 21 contains the digits 1 and 2.
• The integer 474 contains the digit 4 twice and the digit 7 once.
• The integer 400 contains the digit 4 once and the digit 0 twice.
• The integer -77 contains the digit 7 twice.
• The integer 0 is a 0-digit number that contains no digits.
Reminders.
• You may call built-in functions that do not require import, such as min, max, abs, and pow.
• You may call functions defined in earlier parts of the question in your implementation for later parts, and
you may assume that the functions you call are implemented correctly.
RESTRICTION. You may not call str or repr or use [ or ] in any part of this question.
(a) (4.0 points)
Implement count, which takes a digit element and an integer box. It returns the number of times that
element appears in box.
Warning: n % d and n // d may not behave as you expect for negative n. For example, -123 % 10
evaluates to 7. -1 // 10 evaluates to -1. You do not need to know how these operators apply to negative
n in order to solve this problem.
def count(element, box):
"""Count how many times digit element appears in integer box.
>>> count(2, 222122)
>>> count(0, -2020)
>>> count(0, 0)
# 0 has no digits
"""
assert element >= 0 and element < 10
_________
(a)
total = 0
while box > 0:
if _________:
(b)
total = _________
(c)
box = box // 10
return total

## Page 4

i. (2.0 pt) Fill in blank (a).
box = abs(box)
ii. (1.0 pt) Which of these could fill in blank (b)?
# box == element
box % 10 == element
# box % element == 0
# box % element > 0
iii. (1.0 pt) Which of these could fill in blank (c)?
total + 1
# element
# total + element
# box % 10
# total + box % 10

## Page 5

(b) (5.0 points)
Implement count_nine, which takes a digit element and a non-negative integer box. It returns the number
of times that element appears in box and is not adjacent to a 9.
def count_nine(element, box):
"""Count how many times digit element appears in the non-negative integer
box in a place that is not next to a 9.
>>> count_nine(2, 222122)
>>> count_nine(1, 1911191) # Only the middle 1 is not next to a 9
>>> count_nine(9, 9)
>>> count_nine(9, 99)
>>> count_nine(3, 314159265359)
>>> count_nine(5, 314159265359)
>>> count_nine(9, 314159265359)
>>> count_nine(0, 0) # No digits are in 0
"""
assert element >= 0 and element < 10
assert box >= 0
nine, total = False, 0
while box > 0:
if _________ and not (nine or _________):
(a)
(b)
total = _________
(c)
nine = _________ == 9
(d)
box = box // 10
return total
i. (1.0 pt) Which of these could fill in blank (a)?
# box == element
box % 10 == element
# box % element == 0
# box % element > 0

## Page 6

ii. (2.0 pt) Fill in blank (b).
(box // 10) % 10 == 9
iii. (1.0 pt) Which of these could fill in blank (c)?
total + 1
# element
# total + element
# box % 10
# total + box % 10
iv. (1.0 pt) Fill in blank (d).
box % 10

## Page 7

(c) (5.0 points)
Implement fit, which takes two non-negative integers pegs and holes. It returns whether every digit in
pegs appears at least as many times in holes as it does in pegs.
def fit(pegs, holes):
"""Return whether every digit in pegs appears at least as many times in
holes as it does in pegs.
>>> fit(123, 321)
# Each digit appears once in pegs and in holes.
True
>>> fit(1213, 33221) # 1 appears twice in pegs, but only once in holes.
False
>>> fit(12, 22)
# 1 appears once in pegs, but not at all in holes.
False
>>> fit(314159, 112233456789)
True
"""
i = 0
while i <= _________:
(a)
if _________:
(b)
_________
(c)
i = i + 1
return _________
(d)
i. (1.0 pt) Fill in blank (a).
ii. (2.0 pt) Fill in blank (b).
count(i, pegs) > count(i, holes)
iii. (1.0 pt) Fill in blank (c).
return False

## Page 8

iv. (1.0 pt) Which of these could fill in blank (d)?
True
# False
# holes > pegs
# pegs > holes
# holes >= pegs
# pegs >= holes


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](../61a-fa20-final/p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](../61a-fa20-final/p02-stoned.md)
- [61a-fa20-final / P03-COLLEGE-PARTY](../61a-fa20-final/p03-college-party.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](../61a-fa20-final/p04-last-lecture-ama.md)
- [61a-fa20-final / P05-SCHEMEQL](../61a-fa20-final/p05-schemeql.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](../61a-fa20-mt2/p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](../61a-fa20-mt2/p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](../61a-fa20-mt2/p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](../61a-fa20-mt2/p04-fork-it.md)
