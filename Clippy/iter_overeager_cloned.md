Pattern: Early `cloned()` in iterator chain

Issue: -

## Description

It's often inefficient to clone all elements of an iterator, when eventually, only some
of them will be consumed.

## What it does

Checks for usage of `_.cloned().<func>()` where call to `.cloned()` can be postponed.

## Examples

Example of **incorrect** code:

```rust
vec.iter().cloned().take(10);
vec.iter().cloned().last();
```

Example of **correct** code:

```rust
vec.iter().take(10).cloned();
vec.iter().last().cloned();
```

## Known Problems

This `lint` removes the side of effect of cloning items in the iterator.
A code that relies on that side-effect could fail.

## Further Reading

* [Clippy - iter_overeager_cloned](https://clippy.rust-lang.org/stable/index.html#iter_overeager_cloned)
