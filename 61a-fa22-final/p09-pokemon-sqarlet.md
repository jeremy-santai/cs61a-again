---
course: CS61A
term: Fall 2022
assessment: Final
exam_slug: 61a-fa22-final
problem_number: 9
problem_title: "Pokemon SQarLet"
topics: ["lists", "trees", "scheme", "sql"]
---

# Problem 9 — Pokemon SQarLet

## Full Extracted Content
## Page 20

9. (7.0 points)
Pokemon SQarLet
You’ve been hired as the newest Gym Leader of the Paldea region! Now you need to decide what team to make.
All your available Pokemon (for this question, Pokemon stats have been simplified) are listed in a SQL table
Pokemon:
Name
Type1
Type2
Move1
Move2
BaseAttack
BaseDefense
Rattata
Normal
None
Endeavor
Quick Attack
Maushold
Normal
None
Population Bomb
Tidy Up
Cyclizard
Dragon
Normal
Shed Tail
Dragon Rush
Meoscadera
Grass
Dark
Flower Trick
Agility
Farigiraf
Normal
Psychic
Agility
Twin Beam
You also have a table Moves listing all Pokemon moves:
Name
MoveAttack
MoveDefense
Endeavor
Quick Attack
Shed Tail
Dragon Rush
Flower Trick
Agility
Twin Beam
Population Bomb
Tidy Up
Create a table Attack, which lists the Name and TotalAttack of each Pokemon. The total attack of a Pokemon
is equal to the sum of a Pokemon’s BaseAttack and the MoveAttack of both moves it knows. Order rows by
total attack.
For example, Maushold has a base Attack of 30, and has two moves with MoveAttack values 100 and 30,
respectively. Its total attack is 30+100+30 = 160. With the above tables, you should have the following result:
Name
TotalAttack
Maushold
Farigiraf
Cyclizar
Meowscadera
Rattata
CREATE TABLE Attack AS
SELECT __(a)__ AS Name, __(b)__ AS TotalAttack FROM __(c)__ WHERE __(d)__ ORDER BY TotalAttack;
(a) (1.0 pt) Select all options that could fill in Blank (a).
2 Name
■p.Name
2 q.Name
2 a.Name
2 b.Name

## Page 21

(b) (2.0 pt) Fill in Blank (b)
BaseAttack + a.MoveAttack + b.MoveAttack
(c) (2.0 pt) Select all options that could fill in Blank (c).
2 Pokemon, Moves
2 Pokemon, Pokemon, Moves
2 Pokemon, Moves, Moves
2 Pokemon as p, Moves as a
2 Pokemon as p, Pokemon as q, Moves as a
■Pokemon as p, Moves as a, Moves as b
(d) (2.0 pt) Fill in Blank (d)
p.Move1 = a.Name AND p.Move2 = b.Name

## Page 22

10. A+: Treeing up the Wrong Bark
This A+ question is not worth any points. It can only affect your course grade if you have a high
A and might receive an A+. Finish the rest of the exam first!
Write a function table_to_tree that takes a list parents of parent-child relationships between dogs. Each
element of this list is a two-element list of strings containing the name of the parent and the name of the child,
as well as ancestor, the name of the very first dog. It returns a Tree instance with root label ancestor that
has each dog’s name as a label and represents all parent-child pairs in parents as parent-child relations between
nodes. Assume that:
• All dogs have unique names and are descendents of ancestor (or ancestor itself).
• All dogs have exactly one parent (John has some weird dogs) except for ancestor, which has none.
• Any order of branches is acceptable.
For example: table_to_tree([['A','B'],['A','C'],['D','H'],['F','A'],['F','D'],['F','G'],['E','F']],'E')
could return:
Tree('E', [Tree('F', [Tree('A', [Tree('B'), Tree('C')]), Tree('D', [Tree('H')]), Tree('G')])])
def table_to_tree(parents, ancestor):
dogs = {}
def add_if_new(dog):
if __(a)__:
dogs[dog] = __(b)__
for i, j in __(c)__:
add_if_new(i)
add_if_new(j)
__(d)__
__(e)__
(a)
Fill in Blank (a)
not dogs.get(dog)
(b)
Fill in Blank (b)
Tree(dog)
(c)
Fill in Blank (c)
parents
(d)
Fill in Blank (d)
dogs[i].branches.append(dogs[j])

## Page 23

(e)
Fill in Blank (e)
return dogs[ancestor]

## Page 24

11. A+: Another Parentheses Scheme
This A+ question is not worth any points. It can only affect your course grade if you have a high
A and might receive an A+. Finish the rest of the exam first!
After you finish writing your parentheses remover, you run it on all the Scheme code you have. You then realize
that one of those programs was an ongoing assignment. Uh oh! Fortunately, your code for that assignment only
contains two-argument procedures. Write a Scheme macro eval-noparens. This macro receives as input a list
representing a line of Scheme code with all the parentheses removed (except the parentheses surrounding the
entire list), and returns the result that would have been obtained by evaluating the original line of Scheme code.
You are guaranteed that:
• All elements of the list are either numbers or symbols bound to two-input procedures.
• All original call expressions (before parentheses were removed) had exactly two operands.
• The list corresponds to exactly one valid line of Scheme code fulfilling the above conditions.
For credit, your solution must run in linear time in the length of its input.
Hint: Treat the car and cdr of the return value of helper as two independent outputs.
;;; > (eval-noparens (+ 1 * 2 3))
;;; 7
;;; > (eval-noparens (+ * 1 2 + 3 * 4 + + + 5 6 7 8))
;;; 109
;;; > (eval-noparens (cons 1 list 2 3))
;;; (1 2 3)
;;; > (let ((times *)) (eval-noparens (+ 1 times 2 3)))
;;; 7
(define-macro (eval-noparens expr)
(define (helper expr)
(if (number? (car expr)) expr
(let ((x __(a)__ ))
(let ((y __(b)__ ))
__(c)__ ))))
(car (helper expr)))
(a)
Fill in Blank (a)
(helper (cdr expr))
(b)
Fill in Blank (b)
(helper (cdr x))
(c)
Fill in Blank (c)
(cons (list (car expr) (car x) (car y)) (cdr y))

## Page 25

12. A+: Pokemon Ancient SQarLet
This A+ question is not worth any points. It can only affect your course grade if you have a high
A and might receive an A+. Finish the rest of the exam first!
As a gym leader, your team must be composed of Pokemon of a single type. You decide to count how many
Pokemon of each type you have. Generate a table with two columns: All unique types in your collection and
the number of Pokemon you have of each type, sorted in descending order by number of Pokemon.
Each Pokemon can have either one or two types, listed under columns Type1 and Type2.
• If a Pokemon has one type, then Type1 stores the type of the Pokemon, and Type2 stores the string "None".
• If a Pokemon has two types, then Type1 stores the first type of the Pokemon, and Type2 stores the second
type of the Pokemon (which is distinct from the first type).
• A Pokemon with two types counts as both of its types.
The table Pokemon is reprinted here for convenience. All Pokemon have unique names.
Name
Type1
Type2
Move1
Move2
BaseAttack
BaseDefense
Rattata
Normal
None
Endeavor
Quick Attack
Maushold
Normal
None
Population Bomb
Tidy Up
Cyclizard
Dragon
Normal
Shed Tail
Dragon Rush
Meoscadera
Grass
Dark
Flower Trick
Agility
Farigiraf
Normal
Psychic
Agility
Twin Beam
For this table, the following would be the expected output (With the last four rows in any order):
Type
Count
Normal
Dragon
Grass
Dark
Psychic
CREATE TABLE helper AS SELECT __(a)__;
SELECT Type, COUNT(*) AS Count FROM helper __(b)__;
(a)
Fill in Blank (a)
Name, Type1 AS Type FROM Pokemon UNION SELECT Name, Type2 FROM Pokemon
WHERE Type != "None"
(b)
Fill in Blank (b)
GROUP BY Type ORDER BY count(*) DESC;


---

## Same Semester

- [61a-fa22-final / P01-WHAT-WOULD-PYTHON-DO](p01-what-would-python-do.md)
- [61a-fa22-final / P02-WHAT-ABOUT-SCHEME](p02-what-about-scheme.md)
- [61a-fa22-final / P03-SUM-TOTAL](p03-sum-total.md)
- [61a-fa22-final / P04-ADVENT-OF-CODE](p04-advent-of-code.md)
- [61a-fa22-final / P05-TWO-CENTS](p05-two-cents.md)
- [61a-fa22-final / P06-BARKING-UP-THE-WRONG-TREE](p06-barking-up-the-wrong-tree.md)
- [61a-fa22-final / P07-ONE-CENT](p07-one-cent.md)
- [61a-fa22-final / P08-A-PARENTHESES-SCHEME](p08-a-parentheses-scheme.md)
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
