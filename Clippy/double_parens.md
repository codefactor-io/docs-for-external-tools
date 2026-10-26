Pattern: Unnecessary double parentheses

Issue: -

## Description

This makes code harder to read and might indicate a
mistake.

## What it does

Checks for unnecessary double parentheses.

## Examples

Example of **incorrect** code:

```rust
fn simple_double_parens() -> i32 {
    ((0))
}

foo((0));
```

Example of **correct** code:

```rust
fn simple_no_parens() -> i32 {
    (0)
}

foo(0);
```

## Further Reading

* [Clippy - double_parens](https://clippy.rust-lang.org/stable/index.html#double_parens)
