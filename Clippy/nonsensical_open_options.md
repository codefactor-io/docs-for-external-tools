Pattern: Nonsensical file open options

Issue: -

## Description

In the best case, the code will be harder to read than
necessary. I don't know the worst case.

## What it does

Checks for duplicate open options as well as combinations
that make no sense.

## Examples

Example of **incorrect** code:

```rust
use std::fs::OpenOptions;

OpenOptions::new().read(true).truncate(true);
```

## Further Reading

* [Clippy - nonsensical_open_options](https://clippy.rust-lang.org/stable/index.html#nonsensical_open_options)
