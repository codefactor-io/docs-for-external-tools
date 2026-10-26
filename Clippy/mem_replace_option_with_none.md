Pattern: Missing use of `Option::take()`

Issue: -

## Description

`Option` already has the method `take()` for
taking its current value (Some(..) or None) and replacing it with
`None`.

## What it does

Checks for `mem::replace()` on an `Option` with
`None`.

## Examples

Example of **incorrect** code:

```rust
use std::mem;

let mut an_option = Some(0);
let replaced = mem::replace(&mut an_option, None);
```

Example of **correct** code:

```rust
let mut an_option = Some(0);
let taken = an_option.take();
```

## Further Reading

* [Clippy - mem_replace_option_with_none](https://clippy.rust-lang.org/stable/index.html#mem_replace_option_with_none)
