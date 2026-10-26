Pattern: Use of `&Option<T>` in function signature

Issue: -

## Description

More flexibility, better memory optimization, and more idiomatic Rust code.

`&Option<T>` in a function signature breaks encapsulation because the caller must own T
and move it into an Option to call with it. When returned, the owner must internally store
it as `Option<T>` in order to return it.
At a lower level, `&Option<T>` points to memory with the `presence` bit flag plus the `T` value,
whereas `Option<&T>` is usually [optimized](https://doc.rust-lang.org/1.81.0/std/option/index.html#representation)
to a single pointer, so it may be more optimal.

See this [YouTube video](https://www.youtube.com/watch?v=6c7pZYP_iIE) by
Logan Smith for an in-depth explanation of why this is important.

## What it does

Warns when a function signature uses `&Option<T>` instead of `Option<&T>`.

## Examples

Example of **incorrect** code:

```rust
// caller uses  foo(&opt)
fn foo(a: &Option<String>) {}
fn bar(&self) -> &Option<String> { &None }
```

Example of **correct** code:

```rust
// caller should use  `foo1(opt.as_ref())`
fn foo1(a: Option<&String>) {}
// better yet, use string slice  `foo2(opt.as_deref())`
fn foo2(a: Option<&str>) {}
fn bar(&self) -> Option<&String> { None }
```

## Known problems

This lint recommends changing the function signatures, but it cannot
automatically change the function calls or the function implementations.

## Further Reading

* [Clippy - ref_option](https://clippy.rust-lang.org/stable/index.html#ref_option)
