Pattern: Unnecessary mutable reference argument

Issue: -

## Description

The mutable reference rules out all other references to
the value. Also the code misleads about the intent of the call site.

## What it does

Detects passing a mutable reference to a function that only
requires an immutable reference.

## Examples

Example of **incorrect** code:

```rust
vec.push(&mut value);
```

Example of **correct** code:

```rust
vec.push(&value);
```

## Further Reading

* [Clippy - unnecessary_mut_passed](https://clippy.rust-lang.org/stable/index.html#unnecessary_mut_passed)
