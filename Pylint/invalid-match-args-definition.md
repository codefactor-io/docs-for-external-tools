Pattern: Invalid `__match_args__` definition

Issue: -

## Description

The `__match_args__` class attribute must be a tuple of strings. Python uses these strings as attribute names when matching positional class patterns. Defining it as another type, such as a list, causes a `TypeError` when positional matching is attempted.

Use a tuple containing the names of the attributes that can be matched positionally.

## Examples

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ["title", "year"]

    def __init__(self, title, year):
        self.title = title
        self.year = year
```

Example of **correct** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year
```

## Further Reading

* [Pylint - invalid-match-args-definition](https://pylint.readthedocs.io/en/latest/user_guide/messages/error/invalid-match-args-definition.html)
