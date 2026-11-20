Pattern: Name bound to self in class pattern

Issue: -

## Description

Match class patterns are faster if the name binding happens for the whole pattern and any lookup for `__match_args__` can be avoided.

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year


def func(item: Book):
    match item:
        case Book(title=str(title)):  # [match-class-bind-self]
            ...
        case Book(year=int(year)):  # [match-class-bind-self]
            ...
```

Example of **correct** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year


def func(item: Book):
    match item:
        case Book(title=str() as title):
            ...
        case Book(year=int() as year):
            ...
```
