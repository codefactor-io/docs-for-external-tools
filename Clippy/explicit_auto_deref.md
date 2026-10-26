Pattern: Explicit dereference covered by auto-deref

Issue: -

## Description

This unnecessarily complicates the code.

## What it does

Checks for dereferencing expressions which would be covered by auto-deref.

## Examples

Example of **incorrect** code:

```rust
let x = String::new();
let y: &str = &*x;
```

Example of **correct** code:

```rust
let x = String::new();
let y: &str = &x;
```

## Further Reading

* [Clippy - explicit_auto_deref](https://clippy.rust-lang.org/stable/index.html#explicit_auto_deref)
