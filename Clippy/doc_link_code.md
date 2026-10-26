Pattern: Link with code next to other code in docs

Issue: -

## Description

It can be written more simply using HTML-style `<code>` tags.

## What it does

Checks for links with code directly adjacent to code text:
`` [`MyItem`]`<`[`u32`]`>` ``.

## Examples

Example of **incorrect** code:

```rust
//! [`first`](x)`second`
```

Example of **correct** code:

```rust
//! <code>[first](x)second</code>
```

## Further Reading

* [Clippy - doc_link_code](https://clippy.rust-lang.org/stable/index.html#doc_link_code)
