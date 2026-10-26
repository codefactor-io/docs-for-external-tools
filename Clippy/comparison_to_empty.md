Pattern: Comparison with empty string or slice

Issue: -

## Description

Some structures can answer `.is_empty()` much faster
than checking for equality. So it is good to get into the habit of using
`.is_empty()`, and having it is cheap.
Besides, it makes the intent clearer than a manual comparison in some contexts.

## What it does

Checks for comparing to an empty slice such as `""` or `[]`,
and suggests using `.is_empty()` where applicable.

## Examples

Example of **incorrect** code:

```rust
if s == "" {
    ..
}

if arr == [] {
    ..
}
```

Example of **correct** code:

```rust
if s.is_empty() {
    ..
}

if arr.is_empty() {
    ..
}
```

## Further Reading

* [Clippy - comparison_to_empty](https://clippy.rust-lang.org/stable/index.html#comparison_to_empty)
