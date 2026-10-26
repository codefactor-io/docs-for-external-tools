Pattern: `PathBuf::push()` right after creation

Issue: -

## Description

Multiple `.join()` calls are usually easier to read than multiple `.push`
calls across multiple statements. It might also be possible to use
`PathBuf::from` instead.

## What it does

Checks for calls to `push` immediately after creating a new `PathBuf`.

## Examples

Example of **incorrect** code:

```rust
let mut path_buf = PathBuf::new();
path_buf.push("foo");
```

Example of **correct** code:

```rust
let path_buf = PathBuf::from("foo");
// or
let path_buf = PathBuf::new().join("foo");
```

## Known problems

`.join()` introduces an implicit `clone()`. `PathBuf::from` can alternatively be
used when the `PathBuf` is newly constructed. This will avoid the implicit clone.

## Further Reading

* [Clippy - pathbuf_init_then_push](https://clippy.rust-lang.org/stable/index.html#pathbuf_init_then_push)
