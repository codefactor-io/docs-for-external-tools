Pattern: `String` concatenation with `+`

Issue: -

## Description

This particular
`Add` implementation is asymmetric (the other operand need not be `String`,
but `x` does), while addition as mathematically defined is symmetric, and
the `String::push_str(_)` function is a perfectly good replacement.
Therefore, some dislike it and wish not to have it in their code.

That said, other people think that string addition, having a long tradition
in other languages is actually fine, which is why we decided to make this
particular lint `allow` by default.

## What it does

Checks for all instances of `x + _` where `x` is of type
`String`, but only if [`string_add_assign`](#string_add_assign) does *not*
match.

## Examples

Example of **incorrect** code:

```rust
let x = "Hello".to_owned();
x + ", World";
```

Example of **correct** code:

```rust
let mut x = "Hello".to_owned();
x.push_str(", World");
```

## Further Reading

* [Clippy - string_add](https://clippy.rust-lang.org/stable/index.html#string_add)
