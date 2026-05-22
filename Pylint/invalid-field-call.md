Pattern: Malformed use of `field()`

Issue: -

## Description

The `field()` specifier should only be used as the value of an assignment within a dataclass, or within the `make_dataclass()` function.