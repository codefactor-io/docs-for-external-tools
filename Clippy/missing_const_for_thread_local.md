Pattern: Missing `const` in `thread_local!`

Issue: -

## Description

The `thread_local!` macro wraps static declarations and makes them thread-local.
It supports using a `const` keyword that may be used for declarations that can
be evaluated as a constant expression. This can enable a more efficient thread
local implementation that can avoid lazy initialization. For types that do not
need to be dropped, this can enable an even more efficient implementation that
does not need to track any additional state.

https://doc.rust-lang.org/std/macro.thread_local.html

## What it does

Suggests to use `const` in `thread_local!` macro if possible.

## Examples

Example of **incorrect** code:

```rust
thread_local! {
    static BUF: String = String::new();
}
```

Example of **correct** code:

```rust
thread_local! {
    static BUF: String = const { String::new() };
}
```

## Further Reading

* [Clippy - missing_const_for_thread_local](https://clippy.rust-lang.org/stable/index.html#missing_const_for_thread_local)
