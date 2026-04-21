# 2.6 Implementing Classes and Objects

This section demonstrates how classes and objects can be implemented using functions and dictionaries, illustrating that object-oriented programming doesn't require built-in language support. The implementation uses dispatch dictionaries instead of dot notation.

## 2.6.1 Instances

Instances are implemented as dispatch dictionaries with `get` and `set` messages. Attributes are stored in a local dictionary:

```python
def make_instance(cls):
    """Return a new object instance, which is a dispatch dictionary."""
    def get_value(name):
        if name in attributes:
            return attributes[name]
        else:
            value = cls['get'](name)
            return bind_method(value, instance)
    def set_value(name, value):
        attributes[name] = value
    attributes = {}
    instance = {'get': get_value, 'set': set_value}
    return instance
```

When an attribute isn't found locally, the lookup delegates to the class. Function values are bound to the instance via `bind_method`:

```python
def bind_method(value, instance):
    """Return a bound method if value is callable, or value otherwise."""
    if callable(value):
        def method(*args):
            return value(instance, *args)
        return method
    else:
        return value
```

## 2.6.2 Classes

Classes are also dispatch dictionaries, responding to `get`, `set`, and `new` messages:

```python
def make_class(attributes, base_class=None):
    """Return a new class, which is a dispatch dictionary."""
    def get_value(name):
        if name in attributes:
            return attributes[name]
        elif base_class is not None:
            return base_class['get'](name)
    def set_value(name, value):
        attributes[name] = value
    def new(*args):
        return init_instance(cls, *args)
    cls = {'get': get_value, 'set': set_value, 'new': new}
    return cls
```

The `new` message invokes `init_instance`, which creates an instance and calls `__init__`:

```python
def init_instance(cls, *args):
    """Return a new object with type cls, initialized with args."""
    instance = make_instance(cls)
    init = cls['get']('__init__')
    if init:
        init(instance, *args)
    return instance
```

## 2.6.3 Using Implemented Objects

A practical Account class demonstrates the system:

```python
def make_account_class():
    """Return the Account class, with deposit and withdraw methods."""
    interest = 0.02
    def __init__(self, account_holder):
        self['set']('holder', account_holder)
        self['set']('balance', 0)
    def deposit(self, amount):
        """Increase balance by amount and return new balance."""
        new_balance = self['get']('balance') + amount
        self['set']('balance', new_balance)
        return self['get']('balance')
    def withdraw(self, amount):
        """Decrease balance by amount and return new balance."""
        balance = self['get']('balance')
        if amount > balance:
            return 'Insufficient funds'
        self['set']('balance', balance - amount)
        return self['get']('balance')
    return make_class(locals())
```

Usage:

```python
Account = make_account_class()
kirk_account = Account['new']('Kirk')
kirk_account['get']('holder')  # 'Kirk'
kirk_account['get']('deposit')(20)  # 20
kirk_account['get']('withdraw')(5)  # 15
```

### Inheritance

Subclasses override attributes while maintaining access to parent functionality:

```python
def make_checking_account_class():
    """Return CheckingAccount class, imposing $1 withdrawal fee."""
    interest = 0.01
    withdraw_fee = 1
    def withdraw(self, amount):
        fee = self['get']('withdraw_fee')
        return Account['get']('withdraw')(self, amount + fee)
    return make_class(locals(), Account)
```

Usage:

```python
CheckingAccount = make_checking_account_class()
jack_acct = CheckingAccount['new']('Spock')
jack_acct['get']('withdraw')(5)  # 14 (includes $1 fee)
```


---

## Same Chapter

- [Ch2 1 Introduction](ch2-1-introduction.md)
- [Ch2 2 Data Abstraction](ch2-2-data-abstraction.md)
- [Ch2 3 Sequences](ch2-3-sequences.md)
- [Ch2 4 Mutable Data](ch2-4-mutable-data.md)
- [Ch2 5 Object Oriented Programming](ch2-5-object-oriented-programming.md)
- [Ch2 7 Object Abstraction](ch2-7-object-abstraction.md)
- [Ch2 8 Efficiency](ch2-8-efficiency.md)
- [Ch2 9 Recursive Objects](ch2-9-recursive-objects.md)
