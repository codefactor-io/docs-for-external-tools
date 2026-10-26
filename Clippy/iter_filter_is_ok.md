Pattern: Use of `filter(Result::is_ok)`

Issue: -

## Description

This pattern is often followed by manual unwrapping of `Result`. The simplification
results in more readable and succinct code without the need for manual unwrapping.

## What it does

Checks for usage of `.filter(Result::is_ok)` that may be replaced with a `.flatten()` call.
This lint will require additional changes to the follow-up calls as it affects the type.

## Examples

Example of **incorrect** code:

```rust
vec![Ok::<i32, String>(1)].into_iter().filter(Result::is_ok);

```

Example of **correct** code:

```rust
vec![Ok::<i32, String>(1)].into_iter().flatten();
```

## Further Reading

* [Clippy - iter_filter_is_ok](https://clippy.rust-lang.org/stable/index.html#iter_filter_is_ok)
