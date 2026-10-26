Pattern: Misuse of `serde` API

Issue: -

## Description

Serde is very finicky about how its API should be
used, but the type system can't be used to enforce it (yet?).

## What it does

Checks for misuses of the serde API.

## Examples

Implementing `Visitor::visit_string` but not
`Visitor::visit_str`.

## Further Reading

* [Clippy - serde_api_misuse](https://clippy.rust-lang.org/stable/index.html#serde_api_misuse)
