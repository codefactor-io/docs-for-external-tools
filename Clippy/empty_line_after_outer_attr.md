Pattern: Empty line after outer attribute

Issue: -

## Description

The attribute may have meant to be an inner attribute (`#![attr]`). If
it was meant to be an outer attribute (`#[attr]`) then the empty line
should be removed

## What it does

Checks for empty lines after outer attributes

## Examples

Example of **incorrect** code:

```rust
#[allow(dead_code)]

fn not_quite_good_code() {}
```

Example of **correct** code:

```rust
// Good (as inner attribute)
#![allow(dead_code)]

fn this_is_fine() {}

// or

// Good (as outer attribute)
#[allow(dead_code)]
fn this_is_fine_too() {}
```

## Further Reading

* [Clippy - empty_line_after_outer_attr](https://clippy.rust-lang.org/stable/index.html#empty_line_after_outer_attr)
