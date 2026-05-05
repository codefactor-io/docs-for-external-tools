Pattern: Use of `fmt.Errorf`

Issue: -

## Description

This rule identifies calls to `fmt.Errorf` that can be safely replaced by, the more efficient, `errors.New`.

## Further Reading

* [Revive - use-errors-new](https://revive.run/r#use-errors-new)