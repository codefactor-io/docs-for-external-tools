Pattern: Multiple sub-patterns for the same attribute

Issue: -

## Description

A class pattern matches the same attribute more than once. This can happen when a positional pattern and a keyword refer to the same attribute, or when a keyword is repeated. These patterns are invalid and can cause a `TypeError` or `SyntaxError`.

Match each attribute only once.

## Examples

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year


def func(item: Book):
    match item:
        case Book("abc", title="abc"):
            ...
        case Book(year=2000, year=2001):
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

## Further Reading

* [Pylint - multiple-class-sub-patterns](https://pylint.readthedocs.io/en/latest/user_guide/messages/error/multiple-class-sub-patterns.html)
