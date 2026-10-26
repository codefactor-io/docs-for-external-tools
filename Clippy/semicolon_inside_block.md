Pattern: Semicolon placed outside block

Issue: -

## Description

For consistency it's best to have the semicolon inside/outside the block. Either way is fine
and this lint suggests inside the block.
Take a look at `semicolon_outside_block` for the other alternative.

## What it does

Suggests moving the semicolon after a block to the inside of the block, after its last
expression.

## Examples

Example of **incorrect** code:

```rust
unsafe { f(x) };
```

Example of **correct** code:

```rust
unsafe { f(x); }
```

## Further Reading

* [Clippy - semicolon_inside_block](https://clippy.rust-lang.org/stable/index.html#semicolon_inside_block)
