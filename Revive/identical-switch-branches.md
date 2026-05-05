Pattern: Identical switch branches

Issue: -

## Description

`switch` with identical branches makes maintenance harder and might be a source of bugs. Duplicated branches should be consolidated in one case clause.

## Further Reading

* [Revive - identical-switch-branches](https://revive.run/r#identical-switch-branches)