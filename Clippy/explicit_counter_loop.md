Pattern: Missing use of `enumerate()`

Issue: -

## Description

Using `.enumerate()` makes the intent more clear,
declutters the code and may be faster in some instances.

## What it does

Checks `for` loops over slices with an explicit counter
and suggests the use of `.enumerate()`.

## Examples

Example of **incorrect** code:

```rust
let mut i = 0;
for item in &v {
    bar(i, *item);
    i += 1;
}
```

Example of **correct** code:

```rust
for (i, item) in v.iter().enumerate() { bar(i, *item); }
```

## Further Reading

* [Clippy - explicit_counter_loop](https://clippy.rust-lang.org/stable/index.html#explicit_counter_loop)
