Pattern: Printing to stdout

Issue: -

## Description

People often print on *stdout* while debugging an
application and might forget to remove those prints afterward.

## What it does

Checks for printing on *stdout*. The purpose of this lint
is to catch debugging remnants.

## Examples

Example of **incorrect** code:

```rust
println!("Hello world!");
```

## Known problems

Only catches `print!` and `println!` calls.

## Further Reading

* [Clippy - print_stdout](https://clippy.rust-lang.org/stable/index.html#print_stdout)
