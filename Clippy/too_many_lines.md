Pattern: Function with too many lines

Issue: -

## Description

Functions with a lot of lines are harder to understand
due to having to look at a larger amount of code to understand what the
function is doing. Consider splitting the body of the function into
multiple functions.

## What it does

Checks for functions with a large amount of lines.

## Examples

Example of **incorrect** code:

```rust
fn im_too_long() {
    println!("");
    // ... 100 more LoC
    println!("");
}
```

## Further Reading

* [Clippy - too_many_lines](https://clippy.rust-lang.org/stable/index.html#too_many_lines)
