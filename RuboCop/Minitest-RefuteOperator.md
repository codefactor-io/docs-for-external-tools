Pattern: Use of `refute(expected < actual)`

Issue: -

## Description

Enforces the use of `refute_operator(expected, :<, actual`) over `refute(expected < actual)`.

## Examples

``` ruby
# bad
refute(expected < actual)

# good
refute_operator(expected, :<, actual)
```