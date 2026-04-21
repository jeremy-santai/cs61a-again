---
        course: CS61A
        term: Fall 2021
        assessment: MT2
        source_pdf: 61a-fa21-mt2_sol.pdf
        exam_slug: 61a-fa21-mt2
        problem_number: 3
        problem_title: "Shang-Chi"
        page_range: [7, 10]
        topics: ["generators", "lists", "oop"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 3 — Shang-Chi

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: MT2
        - Source PDF: `61a-fa21-mt2_sol.pdf`
        - Pages: 7-10

        ## Full extracted content

        ## Page 7

3. (13.0 points)
Shang-Chi
(a) (6.0 points)
Implement the Valet and Garage classes.
A Valet instance has two instance attributes: their total tips and the garage where they work (a Garage
instance).
• The park method takes a string car and parks it in the Garage where they work.
• The wash method takes a string car that has been parked in their garage and a number tip. The
Valet who washed the car and the Valet who most recently parked the car split the tip.
The Garage constructor takes a list of the Valets who work in that Garage. Assume that park and wash
are only invoked on a Valet that already has a Garage.
class Valet:
"""A valet is tipped after they wash a car,
or after one of their parked cars is washed.
>>> shaun = Valet()
>>> katy = Valet()
>>> g = Garage([shaun, katy])
>>> shaun.park('Benz')
>>> katy.park('BMW')
>>> shaun.wash('Benz', 1)
# $1.0 to Shaun
>>> katy.wash('Benz', 2)
# $1.0 to Katy, $1.0 to Shaun
>>> shaun.park('Rolls')
>>> katy.park('Rolls')
>>> katy.wash('BMW', 2)
# $2.0 to Katy
>>> shaun.wash('Rolls', 2)
# $1.0 to Shaun, $1.0 to Katy
>>> [shaun.tips, katy.tips]
[3.0, 4.0]
"""
def __init__(self):
self.tips = 0
self.garage = None
def park(self, car):
_________
(a)
def wash(self, car, tip):
self.tips += tip / 2
_________ += tip / 2
(b)
class Garage:
"""A garage holds cars parked by the valets who work there."""
def __init__(self, valets):
self.cars = {}
for valet in valets:
_________ = _________
(c)
(d)

## Page 8

i. (2.0 pt) Fill in blank (a).
self.garage.cars[car] = self
ii. (2.0 pt) Fill in blank (b).
self.garage.cars[car].tips
iii. (1.0 pt) Fill in blank (c).
valet.garage
iv. (1.0 pt) Which of these could fill in blank (d)? (Select one.)
# Garage
# valet
# valets
# garage
# self.valet
# self.valets
# self.garage
self

## Page 9

(b) (2.0 points)
Definition. An infinite iterator t is one for which next(t) can be called any number of times and always
returns a value.
Implement ring, a generator function that takes a non-empty list s. It returns an infinite generator that
repeatedly yields the values of s in the order they appear in s.
def ring(s):
"""Yield all values of non-empty s in order, repeatedly.
>>> t = ring([2, 5, 3])
>>> [next(t), next(t), next(t), next(t), next(t), next(t), next(t)]
[2, 5, 3, 2, 5, 3, 2]
"""
_________:
(a)
_________
(b)
i. (1.0 pt) Which of these could fill in blank (a)? (Select one.)
while True
# while s
# for x in s
# for x in ring(s)
ii. (1.0 pt) Fill in blank (b).
yield from s

## Page 10

(c) (5.0 points)
Implement fork, a function that takes an infinite iterator t. It returns two infinite iterators that each
iterate over the contents of t.
def fork(t):
"""Return two iterators with the same contents as infinite iterator t.
>>> a, b = fork(ring([1, 2, 3]))
>>> [next(a), [next(b), next(b), next(b)], next(a), [next(b), next(b), next(b)], next(a)]
[1, [1, 2, 3], 2, [1, 2, 3], 3]
"""
s = []
def copy():
i = 0
while True:
if _________:
(a)
s.append(_________)
(b)
yield _________
(c)
i += 1
return _________
(d)
i. (1.0 pt) Fill in blank (a).
len(s) == i
ii. (1.0 pt) Fill in blank (b).
next(t)
iii. (1.0 pt) Which of these could fill in blank (c)? (Select one.)
# from s
# from t
# s[0]
s[i]
# next(t)
iv. (2.0 pt) Fill in blank (d).
copy(), copy()


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
- [61a-fa21-mt2 / P04-THANOS](p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](p05-groot.md)
