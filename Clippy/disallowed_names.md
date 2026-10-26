Pattern: Use of disallowed name

Issue: -

## Description

These names are usually placeholder names and should be
avoided.

## What it does

Checks for usage of disallowed names for variables, such
as `foo`.

## Examples

Example of **incorrect** code:

```rust
let foo = 3.14;
```

## Further Reading

* [Clippy - disallowed_names](https://clippy.rust-lang.org/stable/index.html#disallowed_names)
