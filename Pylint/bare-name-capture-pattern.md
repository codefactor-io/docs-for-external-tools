Pattern: Unreachable cases after name capture

Issue: -

## Description

A bare name in a `case` pattern captures a value instead of comparing it with an existing variable. Without a guard, this pattern matches every remaining value, making later cases unreachable and causing a `SyntaxError`.

Use a dotted name, such as an enum member, or a literal to match a specific value.

## Examples

Example of **incorrect** code:

```python
red = 0
green = 1
blue = 2


def func(color):
    match color:
        case red:
            print("I see red!")
        case green:
            print("Grass is green")
        case blue:
            print("I'm feeling the blues :(")
```

Example of **correct** code:

```python
from enum import Enum


class Color(Enum):
    RED = 0
    GREEN = 1
    BLUE = 2


def func(color: Color) -> None:
    match color:
        case Color.RED:
            print("I see red!")
        case Color.GREEN:
            print("Grass is green")
        case Color.BLUE:
            print("I'm feeling the blues :(")
```

## Further Reading

* [Pylint - bare-name-capture-pattern](https://pylint.readthedocs.io/en/latest/user_guide/messages/error/bare-name-capture-pattern.html)
