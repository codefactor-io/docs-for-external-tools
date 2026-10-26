Pattern: Unnecessary `&mut` argument

Issue: -

## Description

Less `mut` means less fights with the borrow checker. It can also lead to more
opportunities for parallelization.

## What it does

Check if a `&mut` function argument is actually used mutably.

Be careful if the function is publicly reexported as it would break compatibility with
users of this function, when the users pass this function as an argument.

## Examples

Example of **incorrect** code:

```rust
fn foo(y: &mut i32) -> i32 {
    12 + *y
}
```

Example of **correct** code:

```rust
fn foo(y: &i32) -> i32 {
    12 + *y
}
```

## Further Reading

* [Clippy - needless_pass_by_ref_mut](https://clippy.rust-lang.org/stable/index.html#needless_pass_by_ref_mut)
