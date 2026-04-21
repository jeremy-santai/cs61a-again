---
        course: CS61A
        term: Fall 2021
        assessment: MT2
        source_pdf: 61a-fa21-mt2_sol.pdf
        exam_slug: 61a-fa21-mt2
        problem_number: 2
        problem_title: "Doctor Change"
        page_range: [5, 6]
        topics: ["lists"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 2 — Doctor Change

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: MT2
        - Source PDF: `61a-fa21-mt2_sol.pdf`
        - Pages: 5-6

        ## Full extracted content

        ## Page 5

2. (11.0 points)
Doctor Change
(a) (6.0 points)
Implement change, a function that takes an integer n and a list of positive integers coins. It returns
whether there is a subset of the values in coins that sums to n. As a side effect, change modifies coins.
def change(n, coins):
"""Return whether a subset of coins adds up to n.
>>> change(10, [2, 7, 1, 8, 2])
# e.g., 2 + 8
True
>>> change(20, [2, 7, 1, 8, 2])
# e.g., 2 + 7 + 1 + 8 + 2
True
>>> change(6, [2, 7, 1, 8, 2])
# Impossible; only two 2's in coins
False
"""
if n == 0:
return True
elif _________:
(a)
return False
coin = coins.pop()
# remove the end of coins and name it "coin"
return change(n, _________) _________ change(_________, _________)
(b)
(c)
(d)
(e)
i. (2.0 pt) Fill in blank (a).
n < 0 or not coins or just not coins
ii. (1.0 pt) Fill in blank (b).
list(coins)
At least one of blank (b) and blank (e) must copy the coins list.
iii. (1.0 pt) Fill in blank (c).
or
iv. (1.0 pt) Which of these could fill in blank (d)? (Select one.)
n - coin
# n - coins[0]
# n - coins[1]
# n - coins.pop()
v. (1.0 pt) Fill in blank (e).
list(coins)

## Page 6

(b) (5.0 points)
Implement amounts, which takes a list of positive integers coins. It returns a sorted list of all unique
non-negative integers n for which change(n, coins) returns True. You may not call change.
def amounts(coins):
"""List all unique n such that change(n, coins) returns True (in sorted order).
>>> amounts([2, 5, 3])
[0, 2, 3, 5, 7, 8, 10]
>>> amounts([2, 7, 1, 8, 2])
[0, 1, 2, 3, 4, 5, 7, 8, 9, 10, 11, 12, 13, 15, 16, 17, 18, 19, 20]
"""
if not coins:
return _________
(a)
coin = coins[0]
rest = amounts(_________)
(b)
return sorted(_________ + [k + coin for _________])
(c)
(d)
i. (1.0 pt) Fill in blank (a).
[0]
ii. (1.0 pt) Fill in blank (b).
coins[1:]
iii. (1.0 pt) Which of these could fill in blank (c)? (Select one.)
rest
# rest[1:]
# amounts(rest)
# amounts(rest[1:])
# [k + coin for k in rest]
# [k + coin for k in rest[1:]]
iv. (2.0 pt) Fill in blank (d).
k in rest if k + coin not in rest


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
- [61a-fa21-mt2 / P03-SHANG-CHI](p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](p05-groot.md)
