Pattern: Semicolon placed inside block

Issue: -

## Description

For consistency it's best to have the semicolon inside/outside the block. Either way is fine
and this lint suggests outside the block.
Take a look at `semicolon_inside_block` for the other alternative.

## What it does

Suggests moving the semicolon from a block's final expression outside of the block.

## Examples

Example of **incorrect** code:

```rust
unsafe { f(x); }
```

Example of **correct** code:

```rust
unsafe { f(x) };
```

## Further Reading

* [Clippy - semicolon_outside_block](https://clippy.rust-lang.org/stable/index.html#semicolon_outside_block)
