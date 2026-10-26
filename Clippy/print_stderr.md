Pattern: Printing to stderr

Issue: -

## Description

People often print on *stderr* while debugging an
application and might forget to remove those prints afterward.

## What it does

Checks for printing on *stderr*. The purpose of this lint
is to catch debugging remnants.

## Examples

Example of **incorrect** code:

```rust
eprintln!("Hello world!");
```

## Known problems

Only catches `eprint!` and `eprintln!` calls.

## Further Reading

* [Clippy - print_stderr](https://clippy.rust-lang.org/stable/index.html#print_stderr)
