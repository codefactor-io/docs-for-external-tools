Pattern: Empty `if` branch

Issue: -

## Description

It can be entirely omitted, and often the condition too.

## What it does

Checks for empty `if` branches with no else branch.

## Examples

Example of **incorrect** code:

```rust
if really_expensive_condition(&i) {}
if really_expensive_condition_with_side_effects(&mut i) {}
```

Example of **correct** code:

```rust
// <omitted>
really_expensive_condition_with_side_effects(&mut i);
```

## Known issues

This will usually only suggest to remove the `if` statement, not the condition. Other lints
such as `no_effect` will take care of removing the condition if it's unnecessary.

## Further Reading

* [Clippy - needless_ifs](https://clippy.rust-lang.org/stable/index.html#needless_ifs)
