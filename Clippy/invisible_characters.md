Pattern: Invisible character in string literal

Issue: -

## Description

Having an invisible character in the code makes for all
sorts of April fools, but otherwise is very much frowned upon.

## What it does

Checks for invisible Unicode characters in the code.

## Examples

You don't see it, but there may be a zero-width space or soft hyphen
some­where in this text.

## Further Reading

* [Clippy - invisible_characters](https://clippy.rust-lang.org/stable/index.html#invisible_characters)
