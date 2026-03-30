Pattern: Inconsistent use of `default` on `switch`

Issue: -

## Description

This rule enforces consistent usage of `default` on `switch` statements. It can check for `default` case clause occurrence and/or position in the list of case clauses.

The, non-mutually exclusive, options are:

    "allow-no-default": allows `switch` without `default` case clause.
    "allow-default-not-last": allows `default` case clause to be not the last clause of the `switch`.


## Further Reading

* [Revive - enforce-switch-style](https://revive.run/r#enforce-switch-style)