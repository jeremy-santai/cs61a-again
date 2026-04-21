---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 7
problem_title: "One Cent"
topics: ["higher-order-functions", "generators"]
---

# Problem 7 — One Cent

## Full Extracted Content
## Page 16

7. (10.0 points)
One Cent
In Penney’s Game, two players each choose a different sequence of three coin flips (Heads or Tails). A coin is
flipped repeatedly until one of those two sequences occurs; the winner is the player whose sequence is flipped.
Here’s an example:
Player 1 selects the sequence “HHH” and Player 2 selects the sequence “THH”, then a coin is flipped repeatedly,
yielding the following sequence of coin flips: HTTHTHTTHTHTHH. Since “THH” was flipped first (the last three
flips), Player 2 wins.
(a) (6.0 points)
First, implement the generator function three_flips. It takes as input a (potentially infinite) iterator
coin, each element of which is either 'H' or 'T' (denoting coin flips of Heads and Tails, respectively). It
yields a sequence of triples of coin flip outcomes from coin.
def three_flips(coin):
'''
>>> a = three_flips(iter("HTTHHT"))
>>> next(a)
# Coin flips 0, 1, and 2
'HTT'
>>> next(a)
# Coin flips 1, 2, and 3
'TTH'
>>> next(a)
# Coin flips 2, 3, and 4
'THH'
>>> next(a)
# Coin flips 3, 4, and 5
'HHT'
>>> next(a)
# A StopIteration exception is raised
StopIteration
'''
start = __(a)__
__(b)__:
yield start
start = __(c)__ + __(d)__
i. (2.0 pt) Fill in Blank (a)
next(coin) + next(coin) + next(coin)
ii. (1.0 pt) Fill in Blank (b)
while True
# while next(coin) is not None
# for x in coin
iii. (2.0 pt)
start[1:]

## Page 17

iv. (1.0 pt) Fill in Blank (d)
# coin
# coin.pop()
next(coin)

## Page 18

(b) (4.0 points)
Implement the function penney. It receives as input an iterator coin over 'H' and 'T' and two sequences
p1 and p2. It returns 1 if Player 1 wins Penney’s Game and 2 if Player 2 wins. Assume that one player
wins before the coin runs out of elements, and that p1 and p2 are distinct three-element sequences of ‘H’
and ‘T’.
def penney(coin, p1, p2):
'''Return the winner of Penney's game, where Player 1 chooses p1 and Player 2 chooses p2.
>>> penney(iter("HTTHTHTTHTHTHH"),"THH","HHH")
>>> penney(iter("HTTHTHTTHTHTHH"),"HHH","THH")
>>> penney(iter("HTTHTHTTHTHTHH"),"HTT","THH")
# HTT happens first
'''
it = __(a)__(lambda x: __(b)__, __(c)__)
if next(it) == p1:
return 1
return 2
i. (1.0 pt) Fill in Blank (a)
filter
ii. (2.0 pt) Fill in Blank (b)
x in [p1, p2]
iii. (1.0 pt) Fill in Blank (c)
# it
# coin
# (p1, p2)
three_flips(coin)


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](p04-advent-of-code.md)
- [61a-fa22-final / P05-TWO-CENTS](p05-two-cents.md)
- [61a-fa22-final / P06-BARKING-UP-THE-WRONG-TREE](p06-barking-up-the-wrong-tree.md)
- [61a-fa22-final / P08-A-PARENTHESES-SCHEME](p08-a-parentheses-scheme.md)
- [61a-fa22-final / P09-POKEMON-SQARLET](p09-pokemon-sqarlet.md)
- [61a-fa22-final / P13-OPTIONAL](p13-optional.md)
- [61a-fa22-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa22-mt1/p01-what-would-python-display.md)
- [61a-fa22-mt1 / P02-DON-T-CALL-ME-I-LL-CALL-YOU](../61a-fa22-mt1/p02-don-t-call-me-i-ll-call-you.md)
- [61a-fa22-mt1 / P03-IT-S-PERFECT](../61a-fa22-mt1/p03-it-s-perfect.md)
- [61a-fa22-mt1 / P04-SUPER-POWERS](../61a-fa22-mt1/p04-super-powers.md)
- [61a-fa22-mt1 / P05-A-QUESTION-1-BUSY-BEAVER](../61a-fa22-mt1/p05-a-question-1-busy-beaver.md)
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](../61a-fa22-mt2/p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](../61a-fa22-mt2/p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](../61a-fa22-mt2/p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](../61a-fa22-mt2/p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](../61a-fa22-mt2/p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](../61a-fa22-mt2/p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](../61a-fa22-mt2/p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](../61a-fa22-mt2/p08-optional.md)
