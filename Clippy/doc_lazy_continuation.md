Pattern: Lazy paragraph continuation in docs

Issue: -

## Description

This is easy to write but hard to read. Lazy continuations makes
unintended markers hard to see, and make it harder to deduce the
document's intended structure.

## What it does

In CommonMark Markdown, the language used to write doc comments, a
paragraph nested within a list or block quote does not need any line
after the first one to be indented or marked. The specification calls
this a "lazy paragraph continuation."

## Examples

This table is probably intended to have two rows,
but it does not. It has zero rows, and is followed by
a block quote.
```rust
/// Range | Description
/// ----- | -----------
/// >= 1  | fully opaque
/// < 1   | partially see-through
fn set_opacity(opacity: f32) {}
```

Fix it by escaping the marker:
```rust
/// Range | Description
/// ----- | -----------
/// \>= 1 | fully opaque
/// < 1   | partially see-through
fn set_opacity(opacity: f32) {}
```

This example is actually intended to be a list:
```rust
/// * Do nothing.
/// * Then do something. Whatever it is needs done,
/// it should be done right now.
```

Fix it by indenting the list contents:
```rust
/// * Do nothing.
/// * Then do something. Whatever it is needs done,
///   it should be done right now.
```

## Further Reading

* [Clippy - doc_lazy_continuation](https://clippy.rust-lang.org/stable/index.html#doc_lazy_continuation)
