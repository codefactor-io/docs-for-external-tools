Pattern: Bare name capture pattern makes remaining patterns unreachable

Issue: -

## Description

Emitted when a name capture pattern is used in a match statement and there are case statements below it.

Example of **incorrect** code:

```python
red = 0
green = 1
blue = 2


def func(color):
    match color:
        case red:  # [bare-name-capture-pattern]
            print("I see red!")
        case green:  # [bare-name-capture-pattern]
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
