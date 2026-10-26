Pattern: Missing use of `?` operator

Issue: -

## Description

Using the `?` operator is shorter and more idiomatic.

## What it does

Checks for expressions that could be replaced by the `?` operator.

## Examples

Example of **incorrect** code:

```rust
if option.is_none() {
    return None;
}
```

Example of **correct** code:

```rust
option?;
```

## Further Reading

* [Clippy - question_mark](https://clippy.rust-lang.org/stable/index.html#question_mark)
