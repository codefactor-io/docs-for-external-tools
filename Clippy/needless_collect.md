Pattern: Unnecessary `collect()`

Issue: -

## Description

`collect` causes the allocation of a new data structure,
when this allocation may not be needed.

## What it does

Checks for functions collecting an iterator when collect
is not needed.

## Examples

Example of **incorrect** code:

```rust
let len = iterator.collect::<Vec<_>>().len();
```

Example of **correct** code:

```rust
let len = iterator.count();
```

## Further Reading

* [Clippy - needless_collect](https://clippy.rust-lang.org/stable/index.html#needless_collect)
