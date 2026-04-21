# 2.5 Object-Oriented Programming

Object-oriented programming (OOP) is a method for organizing programs that combines data abstraction, dispatch dictionaries, and mutable data structures. Python's object system provides convenient syntax that enables a metaphor where independent agents interact within the computer, each bundling local state and behavior.

## 2.5.1 Objects and Classes

A class serves as a template for creating objects of a particular type. Every object is an instance of some class. The `Account` class example demonstrates how to model a bank account with methods like `deposit` and `withdraw`.

Instance attributes are name-value pairs specific to an object, accessible via dot notation. Methods are functions that operate on objects and can access and modify attributes. When creating a new Account:

```python
>>> a = Account('Kirk')
>>> a.holder
'Kirk'
>>> a.balance
0
```

## 2.5.2 Defining Classes

User-defined classes are created using class statements. The `__init__` constructor initializes new objects:

```python
>>> class Account:
        def __init__(self, account_holder):
            self.balance = 0
            self.holder = account_holder
```

The `self` parameter refers to the object being created. Instance attributes persist as attributes of `self`.

Each new instance has its own independent attributes, distinguished by object identity, which can be tested using `is` and `is not` operators:

```python
>>> a = Account('Kirk')
>>> b = Account('Spock')
>>> a is not b
True
```

Methods are defined similarly to functions but have special handling when executed within a class. They receive the invoking object as the first parameter:

```python
>>> class Account:
        def deposit(self, amount):
            self.balance = self.balance + amount
            return self.balance
        def withdraw(self, amount):
            if amount > self.balance:
                return 'Insufficient funds'
            self.balance = self.balance - amount
            return self.balance
```

## 2.5.3 Message Passing and Dot Expressions

Dot expressions provide Python's syntax for message passing. A dot expression consists of an expression, a dot, and a name:

```
<expression> . <name>
```

The `getattr` function provides equivalent functionality:

```python
>>> getattr(spock_account, 'balance')
10
```

When a method is invoked via dot notation, Python distinguishes between functions and bound methods. A function is a class attribute, while a bound method couples a function with the instance on which it will be invoked:

```python
>>> type(Account.deposit)
<class 'function'>
>>> type(spock_account.deposit)
<class 'method'>
```

Functions can be called directly by passing self explicitly, while bound methods bind self automatically:

```python
>>> Account.deposit(spock_account, 1001)
1011
>>> spock_account.deposit(1000)
2011
```

Naming conventions: class names use CapWords, method names use lowercase with underscores, and attributes starting with underscores are implementation details meant for internal use only.

## 2.5.4 Class Attributes

Class attributes are shared across all instances and are created by assignment statements in the class suite outside method definitions:

```python
>>> class Account:
        interest = 0.02
```

All instances can access class attributes, but assigning to a class attribute changes the value for all instances:

```python
>>> spock_account.interest
0.02
>>> Account.interest = 0.04
>>> spock_account.interest
0.04
```

Name resolution for dot expressions:

1. Evaluate the expression to get the object
2. Match the name against instance attributes
3. If not found, look up in the class
4. Return the value (or bound method if it's a function)

Instance attributes take precedence over class attributes. Creating an instance attribute with the same name as a class attribute creates a separate attribute:

```python
>>> kirk_account.interest = 0.08
>>> kirk_account.interest
0.08
>>> spock_account.interest
0.04
```

## 2.5.5 Inheritance

Classes can inherit attributes from base classes. A subclass specializes a base class by overriding certain methods while inheriting others. CheckingAccount inherits from Account but charges for withdrawals:

```python
>>> class CheckingAccount(Account):
        withdraw_charge = 1
        interest = 0.01
        def withdraw(self, amount):
            return Account.withdraw(self, amount + self.withdraw_charge)
```

A subclass represents an "is-a" relationship with its base class, while composition (using objects as attributes) represents "has-a" relationships.

## 2.5.6 Using Inheritance

The name lookup procedure for inherited attributes searches progressively up the inheritance chain:

1. If the name is an attribute in the class, return it
2. Otherwise, look up the name in the base class

Overridden attributes remain accessible through class objects, allowing subclasses to call parent implementations:

```python
return Account.withdraw(self, amount + self.withdraw_charge)
```

Object interfaces are collections of attributes and conditions that objects share. Programs are more robust when they depend on interfaces rather than specific types:

```python
>>> def deposit_all(winners, amount=5):
        for account in winners:
            account.deposit(amount)
```

This works with any account type implementing the deposit method.

## 2.5.7 Multiple Inheritance

Python supports multiple inheritance, where a class inherits from multiple base classes:

```python
>>> class AsSeenOnTVAccount(CheckingAccount, SavingsAccount):
        def __init__(self, account_holder):
            self.holder = account_holder
            self.balance = 1
```

When references are ambiguous, Python resolves names left to right, then upwards. The method resolution order (MRO) can be queried:

```python
>>> [c.__name__ for c in AsSeenOnTVAccount.mro()]
['AsSeenOnTVAccount', 'CheckingAccount', 'SavingsAccount', 'Account', 'object']
```

Python uses the C3 Method Resolution Ordering algorithm to determine precedence consistently.

## 2.5.8 The Role of Objects

The object system promotes separation of concerns, where each object encapsulates and manages part of the program's state, and each class defines functions implementing part of the overall logic.

However, classes are not always the best mechanism. Functional abstractions often better represent input-output relationships. Multi-paradigm languages like Python allow programmers to choose organizational approaches appropriate to specific problems.


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 6 Implementing Classes And Objects](ch2-6-implementing-classes-and-objects.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
