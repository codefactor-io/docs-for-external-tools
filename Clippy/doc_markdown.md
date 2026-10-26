Pattern: Missing backticks in documentation

Issue: -

## Description

*Rustdoc* supports markdown formatting, `_`, `::` and
camel-case probably indicates some code which should be included between
ticks. `_` can also be used for emphasis in markdown, this lint tries to
consider that.

## What it does

Checks for the presence of `_`, `::` or camel-case words
outside ticks in documentation.

## Examples

```rust
/// Do something with the foo_bar parameter. See also
/// that::other::module::foo.
// ^ `foo_bar` and `that::other::module::foo` should be ticked.
fn doit(foo_bar: usize) {}
```

```rust
// Link text with `[]` brackets should be written as following:
/// Consume the array and return the inner
/// [`SmallVec<[T; INLINE_CAPACITY]>`][SmallVec].
/// [SmallVec]: SmallVec
fn main() {}
```

## Known problems

Lots of bad docs won’t be fixed, what the lint checks
for is limited, and there are still false positives. HTML elements and their
content are not linted.

In addition, when writing documentation comments, including `[]` brackets
inside a link text would trip the parser. Therefore, documenting link with
`[`SmallVec<[T; INLINE_CAPACITY]>`]` and then [`SmallVec<[T; INLINE_CAPACITY]>`]: SmallVec
would fail.

## Further Reading

* [Clippy - doc_markdown](https://clippy.rust-lang.org/stable/index.html#doc_markdown)
