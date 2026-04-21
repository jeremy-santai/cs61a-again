---
        course: CS61A
        term: Fall 2020
        assessment: Final
        source_pdf: 61a-fa20-final_sol.pdf
        exam_slug: 61a-fa20-final
        problem_number: 3
        problem_title: "College Party"
        page_range: [9, 14]
        topics: ["generators", "linked-lists", "combinatorics", "lists", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 3 — College Party

        ## Source
        - Course: CS61A
        - Term: Fall 2020
        - Assessment: Final
        - Source PDF: `61a-fa20-final_sol.pdf`
        - Pages: 9-14

        ## Full extracted content

        ## Page 9

3. (21.0 points)
College Party
In a US presidential election, each state has a number of electors.
Definition: For some collection of states s, a win by at least k is a (possibly empty) subset w of s such that
the total number of electors for the states in w is at least k more than the total number of electors for the states
not in w but in s.
For example, in the battleground states below, Arizona (AZ), Pennsylvania (PA), and Michigan (MI) have a
total of 11 + 20 + 16 = 47 electors. The remaining states have a total of 6 + 16 + 10 = 32 electors. So, the
subset <AZ PA MI> is a win by 47 - 32 = 15.
class State:
electors = {}
def __init__(self, code, electors):
self.code = code
self.electors = electors
State.electors[code] = electors
battleground = [State('AZ', 11), State('PA', 20), State('NV', 6),
State('GA', 16), State('WI', 10), State('MI', 16)]
The total number of electors for an empty set of states is 0.
The print_all function prints all elements of an iterable.
def print_all(s):
for x in s:
print(x)
(a) (8.0 points)
Implement wins, a generator function that takes a list of State instances states and an integer k. For
every possible win by at least k among the states, it yields a linked list containing strings of the
two-letter codes for the states in that win.
Any order of the wins and any order of the states within a win is acceptable.
A linked list is a Link instance or Link.empty. The Link class appears on the Midterm 2 Study Guide.
def wins(states, k):
"""Yield each linked list of two-letter state codes that describes a win by at least k.
>>> print_all(wins(battleground, 50))
<AZ PA NV GA WI MI>
<AZ PA NV GA MI>
<AZ PA GA WI MI>
<PA NV GA WI MI>
>>> print_all(wins(battleground, 75))
<AZ PA NV GA WI MI>
"""
if _________:
# (a)
yield Link.empty
if states:
first = states[0].electors

## Page 10

for win in wins(states[1:], _________):
#
(b)
yield Link(_________, win)
#
(c)
yield from wins(states[1:], _________)
#
(d)
i. (2.0 pt) Which of the these could fill in blank (a)?
# k >= 0
# k <= 0
# k == 0
# not states
# k >= 0 and not states
k <= 0 and not states
# k == 0 and not states
ii. (2.0 pt) Which of the these could fill in blank (b)?
k - first
# k + first
# k
# -k
# 0
# first
# min(k, first)
# max(k, first)
iii. (2.0 pt) Fill in blank (c).
states[0].code
iv. (2.0 pt) Which of the these could fill in blank (d)?
# k - first
k + first
# k
# -k
# 0
# first
# min(k, first)
# max(k, first)

## Page 11

(b) (7.0 points)
Implement must_win, which takes a list of State instances states and an integer k. It returns a list of
two-letter state codes (strings) for all states that appear in every win by at least k among the states.
Assume wins is implemented correctly.
def must_win(states, k):
"""List all states that must be won in every scenario that wins by k.
>>> must_win(battleground, 50)
['PA', 'GA', 'MI']
>>> must_win(battleground, 75)
['AZ', 'PA', 'NV', 'GA', 'WI', 'MI']
"""
def contains(s, x):
"""Return whether x is a value in linked list s."""
return (_________) and (_________)
#
(a)
(b)
return [_________ for s in states if _________([_________ for w in wins(states, k)])]
#
(c)
(d)
(e)
i. (1.0 pt) Which of these could fill in blank (a)?
# s is Link.empty
s is not Link.empty
# x in s
# x not in s
# x == s.first
# x != s.first
ii. (2.0 pt) Fill in blank (b).
s.first == x or contains(s.rest, x)
iii. (1.0 pt) Fill in blank (c).
s.code
iv. (1.0 pt) Fill in blank (d) with a single function name.
all

## Page 12

v. (2.0 pt) Fill in blank (e).
contains(w, s.code)

## Page 13

(c) (6.0 points)
Definition. A win by at least k is minimal if every state in it is necessary to win by at least k.
The State class and battleground list are repeated here for convenience. Assume that only this code has
been executed. You may not call wins or must_win.
class State:
electors = {}
def __init__(self, code, electors):
self.code = code
self.electors = electors
State.electors[code] = electors
battleground = [State('AZ', 11), State('PA', 20), State('NV', 6),
State('GA', 16), State('WI', 10), State('MI', 16)]
Implement is_minimal, which takes a non-empty list of strings state_codes in which every element is the
code for some State instance, as well as an integer k. It returns whether the states named in state_codes
form a minimal win by k among all State instances that have ever been constructed.
def is_minimal(state_codes, k):
"""Return whether a non-empty list of state_codes describes a minimal win by
at least k.
>>> is_minimal(['AZ', 'NV', 'GA', 'WI'], 0)
# Every state is necessary
True
>>> is_minimal(['AZ', 'GA', 'WI'], 0)
# Not a win
False
>>> is_minimal(['AZ', 'NV', 'PA', 'WI'], 0)
# NV is not necessary
False
>>> is_minimal(['AZ', 'PA', 'WI'], 0)
# Every state is necessary
True
"""
assert state_codes, 'state_codes must not be empty'
votes_in_favor = _________
#
(a)
total_possible_votes = sum(_________)
#
(b)
def win_margin(n):
"Margin of victory if n votes are in favor and the rest are against."
return n - (total_possible_votes - n)
if win_margin(sum(votes_in_favor)) < k:
return False
# Not a win
in_favor_no_smallest = _________
#
(c)
return win_margin(in_favor_no_smallest) < k

## Page 14

i. (2.0 pt) Fill in blank (a). You may not write battleground in your response.
[State.electors[s] for s in state_codes]
ii. (2.0 pt) Fill in blank (b). You may not write battleground in your response.
State.electors.values()
iii. (2.0 pt) Which of these could fill in blank (c). Check all that apply.
Hint: Two states may have the same number of electors.
■sum(votes_in_favor) - min(votes_in_favor)
2 sum(votes_in_favor - min(votes_in_favor))
2 sum(votes_in_favor - [min(votes_in_favor)])
2 sum(votes_in_favor.remove(min(votes_in_favor)))
2 sum([v for v in votes_in_favor if v > min(votes_in_favor)])


---

## Same Semester

- [61a-fa20-final / P01-THE-DROIDS-YOU-RE-LOOKING-FOR](p01-the-droids-you-re-looking-for.md)
- [61a-fa20-final / P02-STONED](p02-stoned.md)
- [61a-fa20-final / P04-LAST-LECTURE-AMA](p04-last-lecture-ama.md)
- [61a-fa20-final / P05-SCHEMEQL](p05-schemeql.md)
- [61a-fa20-mt1 / P01-DOWN-FOR-THE-COUNT](../61a-fa20-mt1/p01-down-for-the-count.md)
- [61a-fa20-mt1 / P02-MYSTERY-FUNCTION](../61a-fa20-mt1/p02-mystery-function.md)
- [61a-fa20-mt1 / P03-PLEASE-REGISTER-TO-VOTE](../61a-fa20-mt1/p03-please-register-to-vote.md)
- [61a-fa20-mt1 / P04-AMAZING-JOB-GROWTH](../61a-fa20-mt1/p04-amazing-job-growth.md)
- [61a-fa20-mt2 / P01-POLITICAL-ENVIRONMENT](../61a-fa20-mt2/p01-political-environment.md)
- [61a-fa20-mt2 / P02-YIELD-FIBONACCI](../61a-fa20-mt2/p02-yield-fibonacci.md)
- [61a-fa20-mt2 / P03-SPARSE-LISTS](../61a-fa20-mt2/p03-sparse-lists.md)
- [61a-fa20-mt2 / P04-FORK-IT](../61a-fa20-mt2/p04-fork-it.md)
