---
course: CS61A
term: Fall 2022
assessment: MT2
exam_slug: 61a-fa22-mt2
problem_number: 6
problem_title: "Point A to Point B"
topics: ["higher-order-functions", "lists", "oop"]
---

# Problem 6 — Point A to Point B

## Full Extracted Content
## Page 14

6. (8.0 points)
Point A to Point B
A graph is a structure consisting of two parts:
• A set of n nodes, which are labeled from 0 to n-1.
• A set of directed edges, which go from one node (the source node) to another node (the destination).
The above is an example of a graph with 6 nodes, with edges represented as arrows. Note that a graph can have:
• Nodes that have no edges to/from them (Node 3)
• Two edges between the same two nodes, with source and destination reversed (The edges between Nodes 0
and 2)
• An edge from a node to itself (Node 5)
However, a graph cannot have two distinct edges from one node to another. For example, we cannot have a
graph where two edges go from Node 0 to Node 1.
We say that a Node j is a destination of Node i if there is a directed edge from Node i to Node j. Thus, in the
above example, Node 0 has two destinations (Nodes 1 and 2), and Node 1 has one destination (Node 4). Note
that Node 0 is not considered a destination of Node 1.
We say that there is a path from Node i to Node j if either i==j, or we can go from Node i to Node j by
following a sequence of edges in the graph. For example, we can get from Node 1 to Node 0 by following the
edges 1->4, then 4->2, then 2->0.
Graphs are often used to represent transportation maps, where nodes represent individual locations, and edges
represent a path you can take to go from one node to another.
A Graph instance is constructed from a number of nodes and begins with no edges. Edges are added, and then
the destinations method lists destinations for a node and the has_path method determines if a path exists
between two nodes.
>>> g = Graph(6)
# A graph with 6 nodes and no edges.
>>> g.add_edge(0, 2)
# Add an edge from node 0 (source) to node 2 (destination)
>>> g.add_edge(2, 0)
# Add an edge from node 2 (source) to node 0 (destination)
>>> g.add_edge(0, 1)
>>> g.add_edge(1, 4)
>>> g.add_edge(4, 2)
>>> g.add_edge(5, 4)
>>> g.add_edge(5, 5)

## Page 15

>>> g.destinations(0)
[1, 2]
>>> g.destinations(5)
[4, 5]
>>> g.destinations(3)
[]
>>> g.has_path(0,2)
# 0 -> 2
True
>>> g.has_path(5,1)
# 5 -> 4 -> 2 -> 0 -> 1
True
>>> g.has_path(3,3)
# 3
True
>>> g.has_path(1,5)
# No path exists
False
(a) (2.0 points)
Implement the destinations method of the Graph class.
class Graph:
"A graph."
def __init__(self, nodes):
self.nodes = nodes
self.edges = []
def add_edge(self, source, destination):
"Add an edge from source to destination."
if source >= 0 and source < self.nodes:
if destination >= 0 and destination < self.nodes:
if (source, destination) not in self.edges:
self.edges.append((source, destination))
def destinations(self, source):
"Returns a list of all destinations of the given node."
assert source >= 0 and source < self.nodes
return ___(a)___
def has_path(self, source, destination):
"Returns True if a path exists from source to destination, and False otherwise."
...
# The implementation of this method is omitted, but assume it works.
i. (2.0 pt) Fill in blank (a).
[i[1] for i in self.edges if i[0] == source]

## Page 16

(b) (6.0 points)
The function compose_path takes in a list of functions funcs and three non-negative integers, x, y, and
maxval. It returns whether there exists a list of numbers s such that:
• s begins with x and ends with y.
• s[i+1] = f(s[i]) for some f in funcs, for every adjacent pair of elements s[i] and s[i+1].
• 0 <= s[i] and s[i] < maxval for all elements s[i].
Assume x and y are less than maxval and that all elements of funcs are one-argument functions that take
in an integer and output an integer. Complete the implementation of compose_path. (Hint: Treat each
function call f(x) as “moving” from x to f(x).)
def compose_path(funcs, x, y, maxval):
"""
>>> f, g, h = lambda x: 2*x-1, lambda x: x*x+1, lambda x: x-4
>>> #3->10->6->11->122->118->114->110->106->102->98
>>> #
g
h
f
g
h
h
h
h
h
h
>>> compose_path([f, g, h], 3, 98, 1000)
True
>>> #The above path hits 122, and no other path exists to get from 3 to 98
>>> compose_path([f, g, h], 3, 98, 122)
False
>>> [i for i in range(100) if compose_path([h], 10, i, 100)]
[2, 6, 10]
"""
g = Graph(___(a)___)
for f in funcs:
___(b)___:
___(c)___
___(d)___
i. (1.0 pt) Fill in blank (a).
maxval
ii. (1.0 pt) Fill in blank (b).
for j in range(maxval)
iii. (2.0 pt) Fill in blank (c).
g.add_edge(j, f(j))
iv. (1.0 pt) Fill in blank (d).
return g.has_path(x, y) The graph contains all allowed transitions j -> f(j)
after iterating through all f and all j. Therefore, has_path returns whether a
sequence of allowed transitions exists.


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
- [61a-fa22-mt2 / P01-WHAT-WOULD-PYTHON-PYTHON](p01-what-would-python-python.md)
- [61a-fa22-mt2 / P02-ENVIRONMENTAL-DISASTER](p02-environmental-disaster.md)
- [61a-fa22-mt2 / P03-HOG-REVISITED](p03-hog-revisited.md)
- [61a-fa22-mt2 / P04-THE-LAMBDANEAN-HYDRA](p04-the-lambdanean-hydra.md)
- [61a-fa22-mt2 / P05-AIM-FOR-100](p05-aim-for-100.md)
- [61a-fa22-mt2 / P07-A-QUESTION-2-DEFORESTATION](p07-a-question-2-deforestation.md)
- [61a-fa22-mt2 / P08-OPTIONAL](p08-optional.md)
