Pattern: Small `Copy` argument passed by reference

Issue: -

## Description

In many calling conventions instances of structs will
be passed through registers if they fit into two or less general purpose
registers.

## What it does

Checks for functions taking arguments by reference, where
the argument type is `Copy` and small enough to be more efficient to always
pass by value.

## Examples

Example of **incorrect** code:

```rust
fn foo(v: &u32) {}
```

Example of **correct** code:

```rust
fn foo(v: u32) {}
```

## Known problems

This lint is target dependent, some cases will lint on 64-bit targets but
not 32-bit or lower targets.

The configuration option `trivial_copy_size_limit` can be set to override
this limit for a project.

This lint attempts to allow passing arguments by reference if a reference
to that argument is returned. This is implemented by comparing the lifetime
of the argument and return value for equality. However, this can cause
false positives in cases involving multiple lifetimes that are bounded by
each other.

Also, it does not take account of other similar cases where getting memory addresses
matters; namely, returning the pointer to the argument in question,
and passing the argument, as both references and pointers,
to a function that needs the memory address. For further details, refer to
[this issue](https://github.com/rust-lang/rust-clippy/issues/5953)
that explains a real case in which this false positive
led to an **undefined behavior** introduced with unsafe code.

## Further Reading

* [Clippy - trivially_copy_pass_by_ref](https://clippy.rust-lang.org/stable/index.html#trivially_copy_pass_by_ref)
