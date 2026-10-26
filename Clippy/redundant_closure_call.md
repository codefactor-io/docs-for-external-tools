Pattern: Immediately invoked closure

Issue: -

## Description

It is unnecessarily adding to the expression's
complexity.

## What it does

Detects closures called in the same expression where they
are defined.

## Examples

Example of **incorrect** code:

```rust
let a = (|| 42)();
```

Example of **correct** code:

```rust
let a = 42;
```

## Further Reading

* [Clippy - redundant_closure_call](https://clippy.rust-lang.org/stable/index.html#redundant_closure_call)
