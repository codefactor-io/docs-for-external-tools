Pattern: Public `Future` not implementing `Send`

Issue: -

## Description

A Future implementation captures some state that it
needs to eventually produce its final value. When targeting a multithreaded
executor (which is the norm on non-embedded devices) this means that this
state may need to be transported to other threads, in other words the
whole Future needs to implement the `Send` marker trait. If it does not,
then the resulting Future cannot be submitted to a thread pool in the
end user’s code.

Especially for generic functions it can be confusing to leave the
discovery of this problem to the end user: the reported error location
will be far from its cause and can in many cases not even be fixed without
modifying the library where the offending Future implementation is
produced.

## What it does

This lint requires Future implementations returned from
functions and methods to implement the `Send` marker trait,
ignoring type parameters.

If a function is generic and its Future conditionally implements `Send`
based on a generic parameter then it is considered `Send` and no warning is emitted.

This can be used by library authors (public and internal) to ensure
their functions are compatible with both multi-threaded runtimes that require `Send` futures,
as well as single-threaded runtimes where callers may choose `!Send` types
for generic parameters.

## Examples

Example of **incorrect** code:

```rust
async fn not_send(bytes: std::rc::Rc<[u8]>) {}
```

Example of **correct** code:

```rust
async fn is_send(bytes: std::sync::Arc<[u8]>) {}
```

## Further Reading

* [Clippy - future_not_send](https://clippy.rust-lang.org/stable/index.html#future_not_send)
