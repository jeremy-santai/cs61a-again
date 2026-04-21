---
course: CS61A
term: Fall 2023
assessment: Final
exam_slug: 61a-fa23-final
problem_number: 4
problem_title: "Six Pages of Pairings (So Please Read the Definition Carefully)"
topics: ["higher-order-functions", "generators", "lists", "oop"]
---

# Problem 4 — Six Pages of Pairings (So Please Read the Definition Carefully)

## Full Extracted Content
## Page 7

4. (29.0 points)
Six Pages of Pairings (So Please Read the Definition Carefully)
Definition: A pairing of a sequence s is a list of two-element tuples (called pairs) that contain adjacent
elements of s. There must be at least one element of s between any two pairs in the pairing. The pairs in the
pairing must be in the same order as they are in s.
The sequence [4, 5, 6, 1, 2, 3, 7, 8] has pairings [(6, 1), (3, 7)] and [(4, 5), (1, 2), (7, 8)]
and [] and many others, but the following are not pairings of that sequence:
• [(5, 1), (3, 7)] contains a pair (5, 1), but 5 and 1 are not adjacent in the sequence.
• [(5, 6), (1, 2)] contains two pairs with no element between them, since 6 is adjacent to 1 in the
sequence.
• [(1, 2), (4, 5)] contains valid pairs, but those pairs are not in the same order as the sequence.
(a) (6.0 points)
Implement longest_pairing, which takes a list s with 3*n-1 elements for some positive integer n. It
returns the longest pairing of s.
def longest_pairing(s):
"""Return the longest pairing for list s that has length 3*n-1 for some positive integer n.
>>> longest_pairing([1, 2, 3, 4, 5, 6, 7, 8])
[(1, 2), (4, 5), (7, 8)]
"""
assert len(s) > 0 and _______, 's must have length 3*n-1 for a positive integer n'
(a)
result, pair, skip = [], [], False
for x in s:
if _______:
(b)
pair.append(x)
else:
_______
(c)
if _______:
(d)
results._______
(e)
pair, skip = [], True
return result

## Page 8

i. (1.0 pt) Fill in blank (a)
# len(s) == 3 * n - 1
# (len(s) - 1) / 3
# (len(s) - 1) % 3 == 0
len(s) % 3 == 2
ii. (1.0 pt) Fill in blank (b)
# skip
not skip
# result
# not result
# pair
# not pair
# len(pair) < 2
# len(pair) == 2
iii. (1.0 pt) Fill in blank (c)
skip = False
# skip = True
# pair = []
# pair.remove(x)
# result.append(x)
# result.append(pair)
iv. (1.0 pt) Fill in blank (d)
# skip
# not skip
# result
# not result
# pair
# not pair
# len(pair) < 2
len(pair) == 2

## Page 9

v. (2.0 pt) Fill in blank (e). Select all that apply.
2 append(pair)
2 extend(pair)
■append((pair[0], pair[1]))
2 extend((pair[0], pair[1]))
■append(tuple(pair))
2 extend(tuple(pair))
2 append(tuple(pair[0], pair[1]))
2 extend(tuple(pair[0], pair[1]))

## Page 10

(b) (4.0 points)
Implement is_pair_sequence, which takes a list s and returns whether it contains only two-element
tuples.
def is_pair_sequence(s):
"""Return whether list s contains only pairs (which are tuples with two elements).
>>> is_pair_sequence([(1, 2), (3, 4)])
True
>>> is_pair_sequence([(1, 2), (3, 4, 5)])
False
>>> is_pair_sequence([(1, 2), "not a tuple"])
False
>>> is_pair_sequence([(1, 2), (3, (4, 5, 6))])
# (3, (4, 5, 6)) is a two-element tuple
True
>>> is_pair_sequence([])
True
"""
return all([_______ for x in s]) and all(map(_______, s))
(f)
(g)
i. (2.0 pt) Fill in blank (f). Select all that apply. Assume tuple has no subclasses.
2 tuple(x)
2 x == tuple
2 x is tuple
■type(x) == tuple
2 x == type(tuple)
■isinstance(x, tuple)
2 isinstance(x, type(tuple))
2 isinstance(type(x), tuple)
ii. (2.0 pt) Fill in blank (g).
# len(s) == 2
# len(x) == 2
# lambda x: len(s) == 2
lambda x: len(x) == 2
# lambda s: lambda x: len(s) == 2
# lambda s: lambda x: len(x) == 2
# lambda x: len(s[i]) == 2
# lambda x: len(x[i]) == 2
# lambda i: lambda x: len(s[i]) == 2
# lambda i: lambda x: len(x[i]) == 2

## Page 11

(c) (6.0 points)
Implement is_pairing, which takes a list s and a list of pairs. It returns whether pairs is a pairing of
s.
def is_pairing(s, pairs):
"""Return whether the list of pairs is a pairing for the list s.
>>> pairs = [(3, 4), (5, 6), (7, 7)]
>>> is_pairing([3, 3, 4, 5, 4, 5, 6, 0, 7, 7, 7], pairs)
True
>>> is_pairing([3, 3, 4, 5, 6, 0, 7, 7, 7], pairs)
# Need an element between pairs
False
>>> is_pairing([3, 2, 4, 0, 5, 6, 0, 7, 7], pairs)
# Elements of a pair must be adjacent
False
>>> is_pairing([7, 7, 3, 3, 4, 5, 4, 5, 6], pairs)
# Pairing isn't in the same order as s
False
"""
assert is_pair_sequence(pairs)
if not pairs:
return True
if _______:
(h)
return False
if _______ == tuple(s[:2]):
(i)
return is_pairing(s[3:], _______)
# Note: [0, 1][3:] evaluates to []
(j)
return _______
(k)
i. (1.0 pt) Fill in blank (h).
# pairs not in s
# pairs[0] not in s
len(s) < 2
# not is_pairing(s, pairs)
ii. (1.0 pt) Fill in blank (i).
pairs[0]
iii. (1.0 pt) Fill in blank (j).
# pairs
# pairs[1]
pairs[1:]
# pairs[:1]

## Page 12

iv. (3.0 pt) Fill in blank (k).
is_pairing(s[1:], pairs)

## Page 13

(d) (7.0 points)
Implement unequal_pairs, a generator function that yields all non-empty pairings of a list s in which
no pair contains two equal elements.
def unequal_pairs(s):
"""Yield all non-empty pairings for a list s in which each pair's values are unequal.
>>> sorted(unequal_pairs([4, 2, 2, 4, 4, 1, 1]))
# Four different pairings!
[[(2, 4)], [(4, 1)], [(4, 2)], [(4, 2), (4, 1)]]
>>> max(unequal_pairs([4, 2, 2, 4, 5, 4, 4, 1, 5, 5, 6]), key=len)
# The longest pairing
[(4, 2), (4, 5), (4, 1), (5, 6)]
"""
if len(s) >= 2:
yield from _______
(l)
if _______:
(m)
pair = (s[0], s[1])
_______
(n)
for rest in unequal_pairs(s[3:]):
# Note: [0, 1][3:] evaluates to []
yield _______
(o)
i. (2.0 pt) Fill in blank (l).
unequal_pairs(s[1:])
ii. (1.0 pt) Fill in blank (m).
# s[0] == s[1]
s[0] != s[1]
# pair[0] == pair[1]
# pair[0] != pair[1]
iii. (2.0 pt) Fill in blank (n).
yield [pair]
iv. (2.0 pt) Fill in blank (o).
[pair] + rest

## Page 14

(e) (6.0 points)
Implement max_pair_sum, which takes a linked list s (either a Link instance or Link.empty). It returns
the largest possible sum of the values in a pairing of s. The Link class appears on the Midterm 2 Study
Guide (p. 2).
def max_pair_sum(s):
"""Return the largest sum of values in a pairing for a linked list of positive numbers s.
>>> L = Link
# Abbreviate Link
>>> max_pair_sum(L(3, L(4, L(5, L(3, L(4, L(5, L(6))))))))
# 4+5 + 5+6
>>> max_pair_sum(L(3, L(4, L(5, L(3, L(4, L(5, L(6, L(3))))))))) # 3+4 + 3+4 + 6+3
"""
if _______:
(p)
return 0
n = _______
(q)
if s.rest.rest is Link.empty:
return n
else:
return max(n + max_pair_sum(_______), max_pair_sum(_______))
(r)
(s)
i. (2.0 pt) Fill in blank (p). Select all that apply.
2 s is Link.empty
2 s.rest is Link.empty
■s is Link.empty or s.rest is Link.empty
2 s.rest is Link.empty or s is Link.empty
ii. (2.0 pt) Fill in blank (q).
s.first + s.rest.first
iii. (1.0 pt) Fill in blank (r).
# s
# s.rest
# s.rest.rest
s.rest.rest.rest
iv. (1.0 pt) Fill in blank (s).
# s
s.rest
# s.rest.rest
# s.rest.rest.rest


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](p02-path-math.md)
- [61a-fa23-final / P03-TALK-LIKE-A-PIRATE-DAY](p03-talk-like-a-pirate-day.md)
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
