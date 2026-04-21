---
course: CS61A
term: Fall 2022
assessment: MT2
exam_slug: 61a-fa22-mt2
problem_number: 1
problem_title: "What would Python Python?"
topics: ["higher-order-functions", "oop"]
---

# Problem 1 — What would Python Python?

## Full Extracted Content
## Page 3

1. (7.0 points)
What would Python Python?
Assume the code below has been executed.
class Snake:
legs = 0
def __init__(self, name):
self.name = name
def __str__(self):
return self.name
def run(self, s):
print("Snakes don't run")
return self.crawl()
def crawl(self):
print(f"{self} crawled")
def eat(self, s):
self.run(s)
print("Nom nom")
class Python(Snake):
def run(self, s):
print(eval(s))
# eval(s) evaluates string s as a Python expression
snek = Snake("atari")
solidsnake = Snake("David")
solidsnake.legs = 2
solidsnake.run = lambda s: print("He ran")
python = Python("pypy")
For each expression below, write the output displayed by the interactive Python interpreter when the
expression is evaluated.
• If an output has multiple lines, write each line separately.
• If an error occurs, write “Error”, but include all output displayed before the error.
• If evaluation would run forever, write “Forever”.
• To display a function value, write “Function”.
Each expression below should be evaluated independently of previously-evaluated expressions.
(a) (1.0 pt) [snek.legs, Snake.legs]
[0, 0]
(b) (2.0 pt) solidsnake.eat("python")
He ran
Nom nom

## Page 4

(c) (2.0 pt) python.eat("snek")
atari
Nom nom
(d) (2.0 pt) Snake.run(python, python)
Snakes don’t run
pypy crawled


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
- [61a-fa22-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa22-mt1/p01-what-would-python-display.md)
- [61a-fa22-mt1 / P02-DON-T-CALL-ME-I-LL-CALL-YOU](../61a-fa22-mt1/p02-don-t-call-me-i-ll-call-you.md)
- [61a-fa22-mt1 / P03-IT-S-PERFECT](../61a-fa22-mt1/p03-it-s-perfect.md)
- [61a-fa22-mt1 / P04-SUPER-POWERS](../61a-fa22-mt1/p04-super-powers.md)
- [61a-fa22-mt1 / P05-A-QUESTION-1-BUSY-BEAVER](../61a-fa22-mt1/p05-a-question-1-busy-beaver.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](p05-aim-for-100.md)
- [61a-fa22-mt2 / P06-POINT-A-TO-POINT-B](p06-point-a-to-point-b.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](p08-optional.md)
