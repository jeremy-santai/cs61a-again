---
        course: CS61A
        term: Fall 2021
        assessment: Final
        source_pdf: 61a-fa21-final_sol.pdf
        exam_slug: 61a-fa21-final
        problem_number: 4
        problem_title: "Spice"
        page_range: [18, 21]
        topics: ["higher-order-functions", "lists", "scheme"]
        santai_chunk_type: exam_problem
        conversion: pdf_to_markdown
        fidelity: high
        ---

        # Problem 4 — Spice

        ## Source
        - Course: CS61A
        - Term: Fall 2021
        - Assessment: Final
        - Source PDF: `61a-fa21-final_sol.pdf`
        - Pages: 18-21

        ## Full extracted content

        ## Page 18

4. (15.0 points)
Spice
Definition. A repeated call is a nested call expression in which each subexpression is either a number, a symbol,
or a call with exactly one operand. For example, (((f 2) 3) 4) is a repeated call.
Reminder. In Scheme, the call expression (f 2) is a 2-element list containing the symbol f and the number
2. Therefore, one expression can evaluate to another expression. For example, the expression (list 'f 2)
evaluates to (f 2).
(a) (4.0 points)
Implement repeated-call, a procedure that takes an operator expression and a list of operand expres-
sions. It returns a repeated call for the operator and operands. If operands is nil, the result is the
operator expression.
;;; Construct a repeated call expression from an operator and a list of operands.
;;;
;;; scm> (repeated-call 'f '(2 3 4))
;;; (((f 2) 3) 4)
;;; scm> (repeated-call '(f 2) '(3 4))
;;; (((f 2) 3) 4)
;;; scm> (repeated-call 'f nil)
;;; f
(define (repeated-call operator operands)
(if (null? operands)
operator
(_________ _________ _________)))
(a)
(b)
(c)
i. (1.0 pt) Which of these could fill in blank (a)?
# cons
# cdr
# list
# append
# map
repeated-call
ii. (2.0 pt) Fill in blank (b).
(list operator (car operands))
iii. (1.0 pt) Which of these could fill in blank (c)?
# operands
(cdr operands)
# (cons operator operands)
# (cons operator (cdr operands))
# (repeated-call operator operands)
# (repeated-call operator (cdr operands))

## Page 19

(b) (4.0 points)
Complete the implementation of curry, a higher-order procedure that is called repeatedly on a non-negative
integer num-args and then a procedure f. It returns a curried version of f that, when called repeatedly
num-args times, returns the result of applying f to those arguments. Assume that f can take num-args
arguments.
As a special case, ((curry 0) f) calls f on no arguments, which is equivalent to evaluating (f).
Hint: The built-in apply procedure takes a procedure f and a list of arguments s and applies f to the
elements of s. For example,
• (apply + '(1 2 3)) is equivalent to (+ 1 2 3) and evaluates to 6.
• (apply + '()) is equivalent to (+) and evaluates to 0.
;;; Return a curried version of f that can be called repeatedly num-args times.
;;;
;;; scm> (((((curry 3) +) 4) 5) 6)
;
(+ 4 5 6) evaluates to 15
;;; 15
;;; scm> ((curry 0) +)
; (+) evaluates to 0
;;; 0
;;; scm> (((curry 1) +) 3)
; (+ 3) evaluates to 3
;;; 3
;;; scm> (((((curry 3) list) 4) 5) 6)
; (list 4 5 6) evaluates to (4 5 6)
;;; (4 5 6)
(define (curry num-args)
(lambda (f) (curry-helper num-args (lambda (s) (apply f s)))))
;;; curry-helper's argument g is a one-argument procedure that takes a list.
;;;
;;; scm> ((((curry-helper 3 cdr) 5) 6) 7)
; (cdr '(5 6 7)) => (6 7)
;;; (6 7)
(define (curry-helper num-args g)
(if (= num-args 0)
_________
(a)
(lambda (x) (curry-helper (- num-args 1) _________))))
(b)
i. (2.0 pt) Fill in blank (a).
(g nil)
ii. (2.0 pt) Fill in blank (b).
(lambda (s) (g (cons x s)))

## Page 20

(c) (7.0 points)
Implement one-arg, which takes a Scheme expression s. It returns a call expression that would evaluate to
the same value as s (calling the same procedures), but which uses curry to ensure that all call expressions
have exactly one operand. Call expressions that already have one operand are unchanged.
• Assume s contains only numbers, symbols, and call expressions; no special forms.
• Assume that each operator (first sub-expression) of a call expression in s is a symbol (such as +).
• Assume that each operand of a call expression in s is either a number or another call expression.
;;; Take a (possibly nested) call expression s and return
;;; an equivalent expression in which all calls have one argument.
;;;
;;; scm> (one-arg '(abs 3))
; (abs 3) already takes just 1 argument
;;; (abs 3)
;;;
;;; scm> (+ 4 5 6)
;;; 15
;;; scm> (one-arg '(+ 4 5 6))
;;; (((((curry 3) +) 4) 5) 6)
;;; scm> (eval (one-arg '(+ 4 5 6)))
; Same value as (+ 4 5 6)
;;; 15
;;;
;;; scm> (one-arg '(+ (- 4) (*) (* 5 6)))
;;; (((((curry 3) +) (- 4)) ((curry 0) *)) ((((curry 2) *) 5) 6))
(define (one-arg s)
(if (number? s) s
(let ((num-args (- (length s) 1)))
(if (= num-args 1)
(_________ _________ (one-arg _________)))
(a)
(b)
(c)
(repeated-call (list _________ _________)
(d)
(e)
(map _________ (cdr s)))))))
(f)
i. (1.0 pt) Which of these could fill in blank (a)?
# cons
# car
# cdr
list
# append
# length

## Page 21

ii. (1.0 pt) Which of these could fill in blank (b)?
# s
(car s)
# (cdr s)
# (car (cdr s))
# (car (cdr (cdr s)))
iii. (1.0 pt) Which of these could fill in blank (c)?
# s
# (car s)
# (cdr s)
(car (cdr s))
# (car (cdr (cdr s)))
iv. (2.0 pt) Fill in blank (d).
(list 'curry num-args) or (cons 'curry (cons num-args nil)) or \(curry
,num-args)‘
v. (1.0 pt) Which of these could fill in blank (e)?
# s
# 's
(car s)
# '(car s)
# (cdr s)
# '(cdr s)
vi. (1.0 pt) Which of these could fill in blank (f)?
one-arg
# car
# cdr
# (lambda (x) (car (cdr x)))
# (lambda (x) (one-arg (car x)))
# (lambda (x) (one-arg (car (cdr x))))


---

## Same Semester

- [61a-fa21-final / P01-HOUSE-ATREIDES](p01-house-atreides.md)
- [61a-fa21-final / P02-ARRAKIS](p02-arrakis.md)
- [61a-fa21-final / P03-CALADAN](p03-caladan.md)
- [61a-fa21-final / P05-GOM-JABBAR](p05-gom-jabbar.md)
- [61a-fa21-final / P06-JUST-FOR-FUN](p06-just-for-fun.md)
- [61a-fa21-mt1 / P01-WHAT-WOULD-PYTHON-DISPLAY](../61a-fa21-mt1/p01-what-would-python-display.md)
- [61a-fa21-mt1 / P02-31-CAL-OLYMPIANS](../61a-fa21-mt1/p02-31-cal-olympians.md)
- [61a-fa21-mt1 / P03-ALL-HAIL-THE-STONE](../61a-fa21-mt1/p03-all-hail-the-stone.md)
- [61a-fa21-mt2 / P01-HAWKEYE](../61a-fa21-mt2/p01-hawkeye.md)
- [61a-fa21-mt2 / P02-DOCTOR-CHANGE](../61a-fa21-mt2/p02-doctor-change.md)
- [61a-fa21-mt2 / P03-SHANG-CHI](../61a-fa21-mt2/p03-shang-chi.md)
- [61a-fa21-mt2 / P04-THANOS](../61a-fa21-mt2/p04-thanos.md)
- [61a-fa21-mt2 / P05-GROOT](../61a-fa21-mt2/p05-groot.md)
