Pattern: Multiple sub-patterns for the same attribute

Issue: -

## Description

Emitted when there is more than one sub-pattern for a specific attribute in a class pattern.

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year


def func(item: Book):
    match item:
        case Book("abc", title="abc"):  # [multiple-class-sub-patterns]
            ...
        case Book(year=2000, year=2001):  # [multiple-class-sub-patterns]
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
        case Book(title="abc"):
            ...
        case Book(year=2000):
            ...
```
