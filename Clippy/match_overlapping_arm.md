Pattern: Overlapping `match` arms

Issue: -

## Description

It is likely to be an error and if not, makes the code
less obvious.

## What it does

Checks for overlapping match arms.

## Examples

Example of **incorrect** code:

```rust
let x = 5;
match x {
    1..=10 => println!("1 ... 10"),
    5..=15 => println!("5 ... 15"),
    _ => (),
}
```

## Further Reading

* [Clippy - match_overlapping_arm](https://clippy.rust-lang.org/stable/index.html#match_overlapping_arm)
