---
course: CS61A
term: Fall 2023
assessment: Final
exam_slug: 61a-fa23-final
problem_number: 2
problem_title: "Path Math"
topics: ["higher-order-functions", "trees"]
---

# Problem 2 — Path Math

## Full Extracted Content
## Page 4

2. (6.0 points)
Path Math
Implement bounds, which takes a Tree instance t and numbers low and high. It returns the number of paths
through t from the root to a leaf for which the sum of the labels along the path is at least low and at most
high.
def bounds(t, low, high):
"""Return the number of root-to-leaf paths in t whose sum is between low and high (inclusive).
>>> t = Tree(3, [Tree(4), Tree(5, [Tree(1), Tree(2)]), Tree(7)])
>>> bounds(t, 7, 10)
# 3+4=7, 3+5+1=9, 3+5+2=10, 3+7=10
>>> bounds(t, 9, 10)
>>> bounds(t, 9, 9)
"""
count = 0
if _______:
(a)
count = 1
return count + _______([_______ for b in t.branches])
(b)
(c)
(a) (2.0 pt) Fill in blank (a).
# low <= t and t <= high
# t and low <= t and t <= high
# t.branches and low <= t and t <= high
# t.is_leaf() and low <= t and t <= high
# low <= t.label and t.label <= high
# t and low <= t.label and t.label <= high
# t.branches and low <= t.label and t.label <= high
t.is_leaf() and low <= t.label and t.label <= high
(b) (1.0 pt) Fill in blank (b).
# bounds
# max
sum
# lambda t:
(c) (3.0 pt) Fill in blank (c).
bounds(b, low - t.label, high - t.label)


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](p01-copying-copies.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](p03-talk-like-a-pirate-day.md)
- [61a-fa23-final / P04-SIX-PAGES-OF-PAIRINGS-SO-PLEASE-READ-THE-DEFINITION-CAREFULLY](p04-six-pages-of-pairings-so-please-read-the-definition-carefully.md)
- [61a-fa23-final / P05-WHAT-WOULD-SCHEME-DO](p05-what-would-scheme-do.md)
- [61a-fa23-final / P06-HOW-TO-GET-PROMOTED](p06-how-to-get-promoted.md)
- [61a-fa23-final / P07-DON-T-SKIP-THIS](p07-don-t-skip-this.md)
- [61a-fa23-final / P08-CHEAP-DONUTS](p08-cheap-donuts.md)
- [61a-fa23-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt1/p01-what-would-python-display.md)
- [61a-fa23-mt1 / P02-AN-ODD-IMPLEMENTATION-OF-EVEN](../61a-fa23-mt1/p02-an-odd-implementation-of-even.md)
- [61a-fa23-mt1 / P03-IN-YOUR-PRIME](../61a-fa23-mt1/p03-in-your-prime.md)
- [61a-fa23-mt1 / P04-CHOOSE-WISELY](../61a-fa23-mt1/p04-choose-wisely.md)
- [61a-fa23-mt2 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa23-mt2/p01-what-would-python-display.md)
- [61a-fa23-mt2 / P02-MAKING-A-LIST-CHECKING-IT-TWICE](../61a-fa23-mt2/p02-making-a-list-checking-it-twice.md)
- [61a-fa23-mt2 / P03-24-HOUR-LIBRARY](../61a-fa23-mt2/p03-24-hour-library.md)
- [61a-fa23-mt2 / P04-A-PERFECT-QUESTION](../61a-fa23-mt2/p04-a-perfect-question.md)
- [61a-fa23-mt2 / P05-ONLY-PATHS](../61a-fa23-mt2/p05-only-paths.md)
- [61a-fa23-mt2 / P06-AFTER-PARTY](../61a-fa23-mt2/p06-after-party.md)
