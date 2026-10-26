Pattern: Parsing `read_line()` result without trim

Issue: -

## Description

The operation will always fail at runtime no matter what the user enters, thus
making it a useless operation.

## What it does

Looks for calls to [`Stdin::read_line`] to read a line from the standard input
into a string, then later attempting to use that string for an operation that will never
work for strings with a trailing newline character in it (e.g. parsing into a `i32`).

## Examples

Example of **incorrect** code:

```rust
let mut input = String::new();
std::io::stdin().read_line(&mut input).expect("Failed to read a line");
let num: i32 = input.parse().expect("Not a number!");
assert_eq!(num, 42); // we never even get here!
```

Example of **correct** code:

```rust
let mut input = String::new();
std::io::stdin().read_line(&mut input).expect("Failed to read a line");
let num: i32 = input.trim_end().parse().expect("Not a number!");
//                  ^^^^^^^^^^^ remove the trailing newline
assert_eq!(num, 42);
```

## Further Reading

* [Clippy - read_line_without_trim](https://clippy.rust-lang.org/stable/index.html#read_line_without_trim)
