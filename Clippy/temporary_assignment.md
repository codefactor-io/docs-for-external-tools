Pattern: Assignment to temporary value

Issue: -

## Description

Readability. If the structure is only created to be
updated, why not write the structure you want in the first place?

## What it does

Checks for construction of a structure or tuple just to
assign a value in it.

## Examples

Example of **incorrect** code:

```rust
(0, 0).0 = 1
```

## Further Reading

* [Clippy - temporary_assignment](https://clippy.rust-lang.org/stable/index.html#temporary_assignment)
