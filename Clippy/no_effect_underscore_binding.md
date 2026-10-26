Pattern: Underscore binding with no effect

Issue: -

## Description

Unlike dead code, these bindings are actually
executed. However, as they have no effect and shouldn't be used further on, all they
do is make the code less readable.

## What it does

Checks for binding to underscore prefixed variable without side-effects.

## Examples

Example of **incorrect** code:

```rust
let _i_serve_no_purpose = 1;
```

## Further Reading

* [Clippy - no_effect_underscore_binding](https://clippy.rust-lang.org/stable/index.html#no_effect_underscore_binding)
