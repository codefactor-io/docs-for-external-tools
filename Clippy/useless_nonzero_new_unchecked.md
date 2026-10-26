Pattern: Use of `NonZero::new_unchecked()` in `const`

Issue: -

## Description

Using `NonZero*::new_unchecked()` is an `unsafe` function and requires an `unsafe` context. When used in a
context evaluated at compilation time, `NonZero*::new().unwrap()` will provide the same result with identical
runtime performances while not requiring `unsafe`.

## What it does

Checks for `NonZero*::new_unchecked()` being used in a `const` context.

## Examples

Example of **incorrect** code:

```rust
use std::num::NonZeroUsize;
const PLAYERS: NonZeroUsize = unsafe { NonZeroUsize::new_unchecked(3) };
```

Example of **correct** code:

```rust
use std::num::NonZeroUsize;
const PLAYERS: NonZeroUsize = NonZeroUsize::new(3).unwrap();
```

## Further Reading

* [Clippy - useless_nonzero_new_unchecked](https://clippy.rust-lang.org/stable/index.html#useless_nonzero_new_unchecked)
