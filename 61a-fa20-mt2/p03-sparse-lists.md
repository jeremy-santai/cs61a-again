---
        course: CS61A
        term: Fall 2020
        assessment: MT2
        source_pdf: 61a-fa20-mt2_sol.pdf
        exam_slug: 61a-fa20-mt2
        problem_number: 3
        problem_title: "Sparse Lists"
        page_range: [9, 12]
        topics: ["lists", "dictionaries", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 3 — Sparse Lists

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: MT2
        - Source PDF: `61a-fa20-mt2_sol.pdf`
        - Pages: 9-12

        ## Full extracted content

        ## Page 9

3. (12.0 points)
Sparse Lists
The most_common function returns the most common element in a non-empty list. You do not need to implement
this function. Assume that it is implemented for you.
def most_common(s):
"""Return the most common element in non-empty list s. In case of a tie,
return the most common element that appears first in s.
>>> most_common([3, 1, 4, 1, 5, 9])
>>> most_common([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5])
>>> most_common([2, 7, 1, 8, 2, 8, 1, 8, 2, 8])
>>> most_common([3, 5, 7, 7, 7, 5, 5])
>>> most_common([3, 7, 5, 5, 7, 7])
"""
Implement the SparseList class. A SparseList instance represents a non-empty list s.
• Its common attribute is the most common value in s.
• Its others dictionary has a value for every element in s that is not common. The corresponding key is the
index for that value in s.
• Its item method takes a non-negative integer i and returns s[i] or the string 'out of range' if i is not
smaller than the length of s.
• Its items method returns a list with the same elements as s in the same order as s.
class SparseList:
"""Represent a non-empty list as a most common value and a dictionary from
indices to values that contains only values that are not the most common.
>>> pi = SparseList([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5])
>>> pi.common
>>> pi.others
{0: 3, 1: 1, 2: 4, 3: 1, 5: 9, 6: 2, 7: 6, 9: 3}
>>> [pi.item(0), pi.item(1), pi.item(2), pi.item(3), pi.item(4)]
[3, 1, 4, 1, 5]
>>> pi.item(10)
>>> pi.item(11)
'out of range'
>>> pi.items()
[3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
"""
def __init__(self, s):
...
def item(self, i):
...
def items(self):
...
(a) (5.0 points)
Implement the __init__ method, which takes a list s.

## Page 10

def __init__(self, s):
assert s, 's cannot be empty'
self.n = len(s)
self.common = most_common(_________)
(a)
self.others = { _________: _________ for i in range(_________) if _________ }
(b)
(c)
(d)
(e)
i. (1.0 pt) Fill in blank (a).
s
ii. (1.0 pt) Which of these could fill in blank (b)?
i
# self.i
# n
# self.n
# s[i]
# s
iii. (1.0 pt) Fill in blank (c).
s[i]
iv. (1.0 pt) Which of these could fill in blank (d)? Check all that apply.
2 s
■len(s)
2 self.s
2 len(self.s)
2 n
2 len(n)
■self.n
2 len(self.n)
v. (1.0 pt) Fill in blank (e).
s[i] != self.common

## Page 11

(b) (3.0 points)
Implement the item method, which takes a non-negative integer i.
def item(self, i):
"""Return s[i] or 'out of range' if i is not smaller than the length of s."""
assert i >= 0, 'index i must be non-negative'
if _________:
(a)
return 'out of range'
elif _________:
(b)
return _________
(c)
else:
return self.common
i. (1.0 pt) Fill in blank (a).
i >= self.n
ii. (1.0 pt) Fill in blank (b).
i in self.others
iii. (1.0 pt) Which of these could fill in blank (c)?
# others[i]
self.others[i]
# others[self.i]
# self.others[self.i]
# others
# self.others

## Page 12

(c) (4.0 points)
Implement the items method.
def items(self):
"""Return a list with the same elements as s in the same order as s."""
return [_________ for i in _________]
(a)
(b)
i. (2.0 pt) Fill in blank (a). You may not use and, or, if, else, [, ], or get.
Hint: Don’t repeat yourself.
self.item(i)
ii. (2.0 pt) Fill in blank (b).
range(self.n)


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
- [61a-fa20-mt2 / P04-FORK-IT](p04-fork-it.md)
