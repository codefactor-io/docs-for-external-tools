Pattern: Unnecessary `Option::as_deref()`

Issue: -

## Description

Redundant code and improving readability.

## What it does

Checks for no-op uses of `Option::{as_deref, as_deref_mut}`,
for example, `Option<&T>::as_deref()` returns the same type.

## Examples

Example of **incorrect** code:

```rust
let a = Some(&1);
let b = a.as_deref(); // goes from Option<&i32> to Option<&i32>
```

Example of **correct** code:

```rust
let a = Some(&1);
let b = a;
```

## Further Reading

* [Clippy - needless_option_as_deref](https://clippy.rust-lang.org/stable/index.html#needless_option_as_deref)
