Pattern: Missing `const` on function

Issue: -

## Description

Not having the function const prevents callers of the function from being const as well.

## What it does

Suggests the use of `const` in functions and methods where possible.

## Examples

```rust
fn new() -> Self {
    Self { random_number: 42 }
}
```

Could be a const fn:

```rust
const fn new() -> Self {
    Self { random_number: 42 }
}
```

## Known problems

Const functions are currently still being worked on, with some features only being available
on nightly. This lint does not consider all edge cases currently and the suggestions may be
incorrect if you are using this lint on stable.

Also, the lint only runs one pass over the code. Consider these two non-const functions:

```rust
fn a() -> i32 {
    0
}
fn b() -> i32 {
    a()
}
```

When running Clippy, the lint will only suggest to make `a` const, because `b` at this time
can't be const as it calls a non-const function. Making `a` const and running Clippy again,
will suggest to make `b` const, too.

If you are marking a public function with `const`, removing it again will break API compatibility.

## Further Reading

* [Clippy - missing_const_for_fn](https://clippy.rust-lang.org/stable/index.html#missing_const_for_fn)
