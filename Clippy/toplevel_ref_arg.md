Pattern: Top-level `ref` binding

Issue: -

## Description

The `ref` declaration makes the function take an owned
value, but turns the argument into a reference (which means that the value
is destroyed when exiting the function). This adds not much value: either
take a reference type, or take an owned value and create references in the
body.

For let bindings, `let x = &foo;` is preferred over `let ref x = foo`. The
type of `x` is more obvious with the former.

## What it does

Checks for function arguments and let bindings denoted as
`ref`.

## Examples

Example of **incorrect** code:

```rust
fn foo(ref _x: u8) {}
```

Example of **correct** code:

```rust
fn foo(_x: &u8) {}
```

## Known problems

If the argument is dereferenced within the function,
removing the `ref` will lead to errors. This can be fixed by removing the
dereferences, e.g., changing `*x` to `x` within the function.

## Further Reading

* [Clippy - toplevel_ref_arg](https://clippy.rust-lang.org/stable/index.html#toplevel_ref_arg)
