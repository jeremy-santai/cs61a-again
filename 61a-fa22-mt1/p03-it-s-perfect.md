---
course: CS61A
term: Fall 2022
assessment: MT1
exam_slug: 61a-fa22-mt1
problem_number: 3
problem_title: "It’s Perfect"
topics: ["oop"]
---

# Problem 3 — It’s Perfect

## Full Extracted Content
## Page 6

3. (10.0 points)
It’s Perfect
Definitions. A perfect number is a positive integer n whose proper factors (the factors of n below n) sum to exactly n.
A number n is abundant if the sum of n’s proper factors is greater than n and deficient if that sum is less than n.
(a) (4.0 points)
Implement classify, a function that takes an integer n greater than 1. It returns the string 'deficient',
'perfect', or 'abundant' that correctly describes n.
def classify(n):
"""Return whether n > 1 is 'deficient', 'perfect', or 'abundant'.
>>> classify(6)
# Proper factors 1, 2 and 3 sum to exactly 6.
'perfect'
>>> classify(24)
# Proper factors 1, 2, 3, 4, 6, 8, and 12 sum to 36.
'abundant'
>>> classify(23)
# Proper factor 1 sums to 1.
'deficient'
"""
total, k = 0, 1
while __<BLANK 1>__:
if __<BLANK 2>__:
__<BLANK 3>__
k = k + 1
if total == n:
return 'perfect'
elif __<BLANK 4>__:
return 'deficient'
else:
return 'abundant'
i. (1.0 pt) BLANK 1
k < n
# k <= n
# k < total
# k <= total
ii. (1.0 pt) BLANK 2
n % k == 0
iii. (1.0 pt) BLANK 3
total += k

## Page 7

iv. (1.0 pt) BLANK 4
total < n
In order to classify a number, we divide the code roughly into two steps:
• Compute the sum of all the proper factors of n
• Compare that sum to n to determine what classification to return
The first step is done with the while loop; we iterate over all values of k from 1 to n (not including n), and
check if each one is a factor of n. This can be done by running n % k; if this is zero, then k divides n evenly,
so k is a factor of n. If k is a factor of n, we add its value to the running total.
The second step is done by checking if total is either equal to, less than, or greater than n. This is done in the
last if/elif/else clause; since we want to return 'deficient' when total < n, we pick that to fill blank 4.

## Page 8

(b) (6.0 points)
Implement nearest_perfect, which takes an integer n above 5. It returns the nearest perfect number to n. If two
perfect numbers are equally close to n, return the larger one. A number a is nearer to n than another number b if
abs(a - n) < abs(b - n). Assume classify is implemented correctly.
def nearest_perfect(n):
"""Return the nearest perfect number to n. In a tie, return the larger one.
>>> nearest_perfect(8)
# 6 is perfect and 2 away from 8.
>>> nearest_perfect(20)
# 28 is perfect and 8 away from 20.
>>> nearest_perfect(17)
# Both 6 and 28 are 11 away from 17.
>>> nearest_perfect(6)
# 6 is perfect and 0 away from 6.
"""
k = 0
while True:
if __<BLANK 5>__:
__<BLANK 6>__
if __<BLANK 7>__:
k = -k
else:
__<BLANK 8>__
i. (2.0 pt) BLANK 5
classify(n+k) == “perfect”
ii. (1.0 pt) BLANK 6
# n = n + k
# n = n + 1
# n = n - k
# n = n - 1
return n + k
# return n
# return k
iii. (1.0 pt) BLANK 7
k > 0; Alternate solution: classify(n-k)==“perfect”

## Page 9

iv. (2.0 pt) BLANK 8
k = -k + 1; Alternate solution: k = k+1
The key observation here is that we can determine if a number k is perfect by checking if classify(k) returns
'perfect'.
We can further note that according to the rules for returning, we should return the first perfect number that
appears in the sequence n, n+1, n-1, n+2, n-2, ...
For example, if we try to get nearest_perfect(17), we should check, in order, 17, 18, 16, 19, 15, 20,
..., 28, 6, .... Among these values, 28 is the first perfect number, so it is the nearest perfect number to
17. Note that we check 17 + 11 == 28 before we check 17 - 11 == 6, so we return the larger perfect number
if n is equally close to two perfect numbers.
Thus, we can fill blanks 5 and 6 so check if n+k is a perfect number, and return n+k, respectively. For blanks 7
and 8, we want to make it so that k goes 0, 1, -1, 2, -2, .... We note that after every positive number k
in this sequence, the next number is -k, so we set blank 7 to check if k > 0. For all other numbers, we go
from 0 -> 1, -1 -> 2, -2 -> 3, and so on. This can be done by negating k and adding 1; that is, 1 == -0 +
1, 2 == -(-1)+1, etc. Thus we fill blank 8 with k = -k + 1.
An alternative solution is to check if classify(n-k)==’perfect’ in line 7. If this is the case, then k gets set
to -k, and we return the appropriate perfect number in the next iteration of the while loop. Using this, line 8
needs only to increment k, so we can do k += 1 on that line.


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](../61a-fa22-final/p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](../61a-fa22-final/p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](../61a-fa22-final/p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](../61a-fa22-final/p04-advent-of-code.md)
- [61a-fa22-final / P05-TWO-CENTS](../61a-fa22-final/p05-two-cents.md)
- [61a-fa22-final / P06-BARKING-UP-THE-WRONG-TREE](../61a-fa22-final/p06-barking-up-the-wrong-tree.md)
- [61a-fa22-final / P07-ONE-CENT](../61a-fa22-final/p07-one-cent.md)
- [61a-fa22-final / P08-A-PARENTHESES-SCHEME](../61a-fa22-final/p08-a-parentheses-scheme.md)
- [61a-fa22-final / P09-POKEMON-SQARLET](../61a-fa22-final/p09-pokemon-sqarlet.md)
- [61a-fa22-final / P13-OPTIONAL](../61a-fa22-final/p13-optional.md)
- [61a-fa22-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](p01-what-would-python-display.md)
- [61a-fa22-mt1 / P02-DON-T-CALL-ME-I-LL-CALL-YOU](p02-don-t-call-me-i-ll-call-you.md)
- [61a-fa22-mt1 / P04-SUPER-POWERS](p04-super-powers.md)
- [61a-fa22-mt1 / P05-A-QUESTION-1-BUSY-BEAVER](p05-a-question-1-busy-beaver.md)
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](../61a-fa22-mt2/p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](../61a-fa22-mt2/p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](../61a-fa22-mt2/p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](../61a-fa22-mt2/p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](../61a-fa22-mt2/p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](../61a-fa22-mt2/p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](../61a-fa22-mt2/p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](../61a-fa22-mt2/p08-optional.md)
