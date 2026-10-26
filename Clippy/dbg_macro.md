Pattern: Use of `dbg!`

Issue: -

## Description

The `dbg!` macro is intended as a debugging tool. It should not be present in released
software or committed to a version control system.

## What it does

Checks for usage of the [`dbg!`](https://doc.rust-lang.org/std/macro.dbg.html) macro.

## Examples

Example of **incorrect** code:

```rust
dbg!(true)
```

Example of **correct** code:

```rust
true
```

## Further Reading

* [Clippy - dbg_macro](https://clippy.rust-lang.org/stable/index.html#dbg_macro)
