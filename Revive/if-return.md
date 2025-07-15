Pattern: Redundant `if ...; err != nil` check

Issue: -

## Description

Checking if an error is _nil_ to just after return the error or nil is redundant.

## Further Reading

* [Revive - if-return](https://revive.run/r#if-return)
* 
