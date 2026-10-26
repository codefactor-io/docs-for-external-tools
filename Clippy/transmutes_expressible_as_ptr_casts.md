Pattern: Transmute instead of pointer cast

Issue: -

## Description

Readability. The code tricks people into thinking that
something complex is going on.

## What it does

Checks for transmutes that could be a pointer cast.

## Examples

Example of **incorrect** code:

```rust
unsafe { std::mem::transmute::<*const [i32], *const [u16]>(p) };
```

Example of **correct** code:

```rust
p as *const [u16];
```

## Further Reading

* [Clippy - transmutes_expressible_as_ptr_casts](https://clippy.rust-lang.org/stable/index.html#transmutes_expressible_as_ptr_casts)
