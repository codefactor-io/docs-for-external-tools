Pattern: Use of `bool::then()` in `filter_map()`

Issue: -

## Description

This can be written with `filter` then `map` instead, which would reduce nesting and
separates the filtering from the transformation phase. This comes with no cost to
performance and is just cleaner.

## What it does

Checks for usage of `bool::then` in `Iterator::filter_map`.

## Examples

Example of **incorrect** code:

```rust
_ = v.into_iter().filter_map(|i| (i % 2 == 0).then(|| really_expensive_fn(i)));
```

Example of **correct** code:

```rust
_ = v.into_iter().filter(|i| i % 2 == 0).map(|i| really_expensive_fn(i));
```

## Limitations

Does not lint `bool::then_some`, as it eagerly evaluates its arguments rather than lazily.
This can create differing behavior, so better safe than sorry.

## Further Reading

* [Clippy - filter_map_bool_then](https://clippy.rust-lang.org/stable/index.html#filter_map_bool_then)
