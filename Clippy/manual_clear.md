Pattern: Use of `truncate(0)` instead of `clear()`

Issue: -

## Description

`clear()` expresses the intent better and is likely to be more efficient than `truncate(0)`.

## What it does

Checks for `.truncate(0)` calls on standard library types where it can be replaced with `.clear()`.

Currently this includes `Vec`, `VecDeque`, `String`, and `OsString`.

## Examples

Example of **incorrect** code:

```rust
let mut v = vec![1, 2, 3];
v.truncate(0);
```

Example of **correct** code:

```rust
let mut v = vec![1, 2, 3];
v.clear();
```

## Further Reading

* [Clippy - manual_clear](https://clippy.rust-lang.org/stable/index.html#manual_clear)
