Pattern: `match` scrutinee wrapped in block

Issue: -

## Description

It is unusual to write `{ expr }` when you could just have written
`expr`, and it is unlikely that anyone would write that for any reason
other than wanting temporaries in `expr` to be dropped before executing
the body of the `match`/`if let`/`while` statement. However, prior to
the 2024 edition, wrapping the scrutinee in a block did not drop
temporaries before the body executes.

## What it does

Warns when a match, if let, or while let scrutinee is wrapped in a block.
This lint only triggers on the 2021 edition and older.

## Examples

Example of **incorrect** code:

```rust
if let Some(x) = { my_function() } { .. }
```

## Further Reading

* [Clippy - block_scrutinee](https://clippy.rust-lang.org/stable/index.html#block_scrutinee)
