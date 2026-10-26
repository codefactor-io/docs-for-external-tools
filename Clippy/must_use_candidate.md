Pattern: Missing `#[must_use]` attribute

Issue: -

## Description

Not bad at all, this lint just shows places where
you could add the attribute.

## What it does

Checks for public functions that have no
`#[must_use]` attribute, but return something not already marked
must-use, have no mutable arg and mutate no statics.

## Examples

Example of **incorrect** code:

```rust
// this could be annotated with `#[must_use]`.
pub fn id<T>(t: T) -> T { t }
```

## Known problems

The lint only checks the arguments for mutable
types without looking if they are actually changed. On the other hand,
it also ignores a broad range of potentially interesting side effects,
because we cannot decide whether the programmer intends the function to
be called for the side effect or the result. Expect many false
positives. At least we don't lint if the result type is unit or already
`#[must_use]`.

## Further Reading

* [Clippy - must_use_candidate](https://clippy.rust-lang.org/stable/index.html#must_use_candidate)
