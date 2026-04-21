---
        course: CS61A
        term: Fall 2021
        assessment: MT2
        source_pdf: 61a-fa21-mt2_sol.pdf
        exam_slug: 61a-fa21-mt2
        problem_number: 4
        problem_title: "Thanos"
        page_range: [11, 13]
        topics: ["higher-order-functions", "lists"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 4 — Thanos

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: MT2
        - Source PDF: `61a-fa21-mt2_sol.pdf`
        - Pages: 11-13

        ## Full extracted content

        ## Page 11

4. (10.0 points)
Thanos
Hint: you may call built-in sequence functions: sum, max, min, all, any, map, filter, zip, and reversed.
(a) (4.0 points)
Implement snap, which takes a one-argument function f, a one-argument function g, and a sequence s. It
returns a list of (x, f(x)) pairs (two-element tuples) for all x in s for which g(f(x)) is a true value. The
implementation of snap only calls f once per element of s; never twice.
Important: For full credit, your implementation may only call f once on each element of s.
def snap(f, g, s):
"""Return a list of (x, f(x)) pairs for each x in s such that g(f(x)) is a true value.
>>> snap(lambda x: x * x, lambda x: x < 10, range(5))
[(0, 0), (1, 1), (2, 4), (3, 9)]
>>> snap(lambda x: x * x, lambda x: x > 10, range(5))
[(4, 16)]
>>> snap(lambda x: x * x, lambda x: x and x - 9, range(5))
[(1, 1), (2, 4), (4, 16)]
"""
return [(x, _________) for _________ in _________ if _________]
(a)
(b)
(c)
(d)
i. (1.0 pt) Fill in blank (a).
y
ii. (1.0 pt) Which of these could fill in blank (b)? (Select one.)
# x
x, y
# y
# y, z
iii. (1.0 pt) Fill in blank (c).
zip(s, map(f, s)) or [(z, f(z)) for z in s]
iv. (1.0 pt) Fill in blank (d).
g(y)

## Page 12

(b) (4.0 points)
Implement max_diff, which takes a non-empty sequence s and a one-argument function f. It returns
a pair of elements (v, w) in s for which f(v) - f(w) is largest. v and w may be the same or different
elements of s. Also, describe the order of growth of the run time of max_diff.
def max_diff(s, f):
"""Return two elements (v, w) of s for which f(v) - f(w) is largest.
>>> max_diff(range(-7, 4), lambda x: x * x)
# (-7 * -7) - (0 * 0) = 49
(-7, 0)
>>> max_diff(['what', 'a', 'great', 'film'], len)
# len('great') - len('a')
('great', 'a')
"""
assert s, 's cannot be empty'
v, w = None, None
for x in s:
for y in s:
if v is None or _________:
(a)
_________
(b)
return v, w
i. (1.0 pt) Fill in blank (a).
f(x) - f(y) > f(v) - f(w)
ii. (1.0 pt) Fill in blank (b).
v, w = x, y
iii. (2.0 pt) What is the order of growth of the time required to evaluate max_diff(s, f) for a sequence
s of length n and a function f that requires constant time to evaluate.
# Exponential, Θ(bn)
Quadratic, Θ(n2)
# Linear, Θ(n)
# Logarithmic, Θ(log2 n)
# Constant, Θ(1)

## Page 13

(c) (2.0 points)
Implement max_diff_fast, which has the same signature and behavior as max_diff, but has a faster
order of growth of its run time.
Important. You may not use a list comprehension in your solution.
def max_diff_fast(s, f):
return _________ , _________
(a)
(b)
i. (1.0 pt) Fill in blank (a), but do not use a comprehension.
max(s, key=f)
ii. (1.0 pt) Fill in blank (b), but do not use a comprehension.
min(s, key=f)


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
- [61a-fa21-mt2 / P03-SHANG-CHI](p03-shang-chi.md)
- [61a-fa21-mt2 / P05-GROOT](p05-groot.md)
