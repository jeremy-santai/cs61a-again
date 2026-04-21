---
course: CS61A
term: Fall 2023
assessment: Final
exam_slug: 61a-fa23-final
problem_number: 8
problem_title: "Cheap Donuts"
topics: ["higher-order-functions", "generators", "lists"]
---

# Problem 8 — Cheap Donuts

## Full Extracted Content
## Page 20

8. (6.0 points)
Cheap Donuts
There are three tables in a database:
• The donuts table has a row for each menu option at a donut shop. There are columns for the kind (string)
of dough and flavor (string). For example, there is one row for chocolate cake donuts (although the store
may have many such donuts, they only have one menu option for this kind & flavor combination).
• The price of a donut depends only on the dough. The prices table has a row for each kind of dough. The
dough (string) column contains the kind; the price (number) column is for one donut made from that
kind of dough.
• Your friends only care about the flavor, not the kind of dough. The quantity table contains one row for
every flavor your friends want. The choice (string) column is the flavor they want and the k (number)
column is the number of donuts of that flavor they want.
Create a table with two columns, flavor (string) and total (number) with one row for each flavor your friends
want. The total column contains the least expensive total cost of buying k donuts of that flavor, where k is
the number your friends want.
The rows of the result can appear in any order. Here is an example, but complete the query so that it would
work even if the contents or number of rows were different.
SELECT flavor, _______ AS total FROM _______ WHERE _______ GROUP BY _______;
(a)
(b)
(c)
(d)
(a) (2.0 pt) Fill in blank (a).
MIN(price) * k
(b) (1.0 pt) Fill in blank (b).
# quantity, prices
quantity, donuts, prices
# donuts, prices AS a, prices AS b
# quantity, prices AS a, prices AS b
(c) (2.0 pt) Fill in blank (c).
kind=dough AND choice=flavor

## Page 21

(d) (1.0 pt) Fill in blank (d).
# quantity
# dough
# kind
flavor

## Page 22

9. A+ Questions
These are two separate A+ questions. They can only affect your course grade if you have a high A and
might receive an A+. Finish the rest of the exam first! There is a third A+ question earlier in the exam on
Page 13.
(a)
Complete the definition of fib so that (prefix fib 10) is a list of the first 10 Fibonacci numbers: (0 1
1 2 3 5 8 13 21 34). A Fibonacci number is the sum of the previous two. You may not write lambda
or let or define.
(define-macro (wait expr) `(lambda () ,expr))
(define (prefix s k) (if (zero? k) nil (cons (car s) (prefix ((cdr s)) (- k 1)))))
(define (add s t) (cons (+ (car s) (car t)) (wait (add ((cdr s)) ((cdr t))))))
(define fib (cons 0 (wait (cons 1 _______))))
(wait (add fib ((cdr fib))))
(b)
This question uses the definitions and functions from the earlier question called Six Pages of Pairings.
Fill in blank (a) of match, a generator function that takes a list s and a pairing pairs. It yields all
non-empty pairings of s that contain the pairs in pairs in order, but which may also contain other pairs
as well.
Just fill in just blank (a) as your answer. The remaining blanks are not scored.
def match(s, pairs):
"""Yield all non-empty pairings of s that contain pairs in order.
>>> for p in sorted(match(range(14), [(3, 4), (8, 9)])):
...
print(p)
[(0, 1), (3, 4), (8, 9)]
[(0, 1), (3, 4), (8, 9), (11, 12)]
[(0, 1), (3, 4), (8, 9), (12, 13)]
[(3, 4), (8, 9)]
[(3, 4), (8, 9), (11, 12)]
[(3, 4), (8, 9), (12, 13)]
"""
assert is_pair_sequence(pairs)
if len(s) >= 2:
first = tuple(s[:2])
if _______:
# Just fill in this blank as your answer
(a)
yield [first]
if _______:
rest = pairs[1:]
else:
rest = pairs
for p in match(_______, rest):
yield _______ + p
yield from match(_______, pairs)
(len(pairs) == 1 and pairs[0] == first) or not pairs

## Page 23

No more questions.


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](p02-path-math.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](p03-talk-like-a-pirate-day.md)
- [61a-fa23-final / P04-SIX-PAGES-OF-PAIRINGS-SO-PLEASE-READ-THE-DEFINITION-CAREFULLY](p04-six-pages-of-pairings-so-please-read-the-definition-carefully.md)
- [61a-fa23-final / P05-WHAT-WOULD-SCHEME-DO](p05-what-would-scheme-do.md)
- [61a-fa23-final / P06-HOW-TO-GET-PROMOTED](p06-how-to-get-promoted.md)
- [61a-fa23-final / P07-DON-T-SKIP-THIS](p07-don-t-skip-this.md)
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
