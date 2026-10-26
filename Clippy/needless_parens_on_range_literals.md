Pattern: Unnecessary parentheses around range literal

Issue: -

## Description

Having superfluous parenthesis makes the code less readable
overhead when reading.

## What it does

The lint checks for parenthesis on literals in range statements that are
superfluous.

## Examples

Example of **incorrect** code:

```rust
for i in (0)..10 {
  println!("{i}");
}
```

Example of **correct** code:

```rust
for i in 0..10 {
  println!("{i}");
}
```

## Further Reading

* [Clippy - needless_parens_on_range_literals](https://clippy.rust-lang.org/stable/index.html#needless_parens_on_range_literals)
