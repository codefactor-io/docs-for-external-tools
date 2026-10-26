Pattern: Missing use of `_unchecked` function variant

Issue: -

## Description

Calling the non-unchecked variant may result in checking that is then discarded
if `unwrap_unchecked` is called directly afterwards, whereas the unchecked
variant most likely avoids performing the check completely.

## What it does

Checks for calls to `unwrap_unchecked` when an `_unchecked` variant of the function exists.

## Examples

Example of **incorrect** code:

```rust
let s = unsafe { std::str::from_utf8(&[]).unwrap_unchecked() };
```

Example of **correct** code:

```rust
let s = unsafe { std::str::from_utf8_unchecked(&[]) };
```

## Known problems

The unchecked variant is only suggested if it's defined in the same `impl` block
as the non-unchecked one

## Further Reading

* [Clippy - unnecessary_unwrap_unchecked](https://clippy.rust-lang.org/stable/index.html#unnecessary_unwrap_unchecked)
