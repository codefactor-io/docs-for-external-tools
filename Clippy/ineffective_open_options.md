Pattern: Both `write(true)` and `append(true)` used

Issue: -

## Description

`.append(true)` already enables `write(true)`, making this one
superfluous.

## What it does

Checks if both `.write(true)` and `.append(true)` methods are called
on a same `OpenOptions`.

## Examples

Example of **incorrect** code:

```rust
let _ = OpenOptions::new()
           .write(true)
           .append(true)
           .create(true)
           .open("file.json");
```

Example of **correct** code:

```rust
let _ = OpenOptions::new()
           .append(true)
           .create(true)
           .open("file.json");
```

## Further Reading

* [Clippy - ineffective_open_options](https://clippy.rust-lang.org/stable/index.html#ineffective_open_options)
