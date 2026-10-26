Pattern: Use of `filter(Option::is_some)`

Issue: -

## Description

This pattern is often followed by manual unwrapping of the `Option`. The simplification
results in more readable and succinct code without the need for manual unwrapping.

## What it does

Checks for usage of `.filter(Option::is_some)` that may be replaced with a `.flatten()` call.
This lint will require additional changes to the follow-up calls as it affects the type.

## Examples

Example of **incorrect** code:

```rust
vec![Some(1)].into_iter().filter(Option::is_some);

```

Example of **correct** code:

```rust
vec![Some(1)].into_iter().flatten();
```

## Further Reading

* [Clippy - iter_filter_is_some](https://clippy.rust-lang.org/stable/index.html#iter_filter_is_some)
