Pattern: Positional name capture instead of `as` pattern

Issue: -

## Description

A built-in class pattern such as `str(title)` captures the matched object through a positional sub-pattern. An `as` pattern expresses the same type check and name binding more directly, without unnecessary positional matching.

Use `str() as title` instead of `str(title)`, and the equivalent form for other supported built-in types.

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
        case Book(title=str(title)):
            ...
        case Book(year=int(year)):
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

## Further Reading

* [Pylint - match-class-bind-self](https://pylint.readthedocs.io/en/latest/user_guide/messages/refactor/match-class-bind-self.html)
