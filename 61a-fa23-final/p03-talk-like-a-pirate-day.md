---
course: CS61A
term: Fall 2023
assessment: Final
exam_slug: 61a-fa23-final
problem_number: 3
problem_title: "Talk Like a Pirate Day"
topics: ["lists", "oop"]
---

# Problem 3 — Talk Like a Pirate Day

## Full Extracted Content
## Page 5

3. (10.0 points)
Talk Like a Pirate Day
Pirate expressions are reversed and substitute some words (such as "aye" for "yes") according to a pirate
dialect.
• An Expression instance is constructed from a list of strings and has a dictionary attribute dialect and a
Word instance attribute first that represents the first word of the reversed sequence.
• A Word instance is constructed from its attributes: a string w, an Expression instance exp, and a Word
instance then representing the next word in the reversed sequence. If there is no next word, then is None.
A Word instance’s say method returns either w or its substitute if w is a key of the expression’s dialect.
Printing a Word prints how a pirate would say that word and the following words in the reversed sequence.
Printing an Expression prints all of the words in the reversed sequence using the Expression’s dialect.
Reminder: The get method of a dictionary takes two arguments: key and default. If the key is in the
dictionary, its value is returned. If not, default is returned. E.g., {1:2}.get(1, 3) evaluates to 2, but
{1:2}.get(5, 3) is 3.
class Expression:
"""A pirate expression is reversed and substitutes some words using a dialect.
>>> str(Expression(['I', 'said', 'hi']))
'ahoy says I'
>>> e = Expression(['there', 'you', 'are'])
>>> print(e)
arrrr you there
>>> e.dialect['you'] = 'ye'
# After adding to the dialect...
>>> print(e)
# ... the result of printing changes
arrrr ye there
"""
def __init__(self, original):
assert len(original) > 0
self.dialect = {'yes': 'aye', 'hi': 'ahoy', 'said': 'says', 'are': 'arrrr'}
previous = None
for w in original:
current = _______
(a)
_______
(b)
self.first = _______
(c)
def __str__(self):
return _______
(d)
class Word:
def __init__(self, w, exp, then):
self.w = w
self.exp = exp
self.then = then
def say(self):
return _______
(e)
def __str__(self):
first = _______
(f)
if self.then:
return first + ' ' + str(self.then)

## Page 6

else:
return first
(a) (3.0 pt) Fill in blank (a).
Word(w, self, previous)
(b) (1.0 pt) Fill in blank (b).
previous = current
(c) (1.0 pt) Fill in blank (c).
current
# self.current
# current.then
# self.current.then
(d) (1.0 pt) Fill in blank (d).
# self
# self.first
# str(self)
str(self.first)
# print(self)
# print(self.first)
(e) (3.0 pt) Fill in blank (e).
self.exp.dialect.get(self.w, self.w)
(f) (1.0 pt) Fill in blank (f).
# self.w
# self.exp[w]
# self.say
self.say()
# self.say(self)
# self.say(self.w)


---

## Same Semester

- [61a-fa23-final / P01-COPYING-COPIES](p01-copying-copies.md)
- [61a-fa23-final / P02-PATH-MATH](p02-path-math.md)
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
