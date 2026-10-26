Pattern: `match` on boolean expression

Issue: -

## Description

It makes the code less readable.

## What it does

Checks for matches where match expression is a `bool`. It
suggests to replace the expression with an `if...else` block.

## Examples

```rust
let condition: bool = true;
match condition {
    true => foo(),
    false => bar(),
}
```
Use if/else instead:
```rust
let condition: bool = true;
if condition {
    foo();
} else {
    bar();
}
```

## Further Reading

* [Clippy - match_bool](https://clippy.rust-lang.org/stable/index.html#match_bool)
