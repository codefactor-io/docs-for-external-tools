Pattern: Unnecessary `str::splitn()`

Issue: -

## Description

The function `split` is simpler and there is no performance difference in these cases, considering
that both functions return a lazy iterator.

## What it does

Checks for usage of `str::splitn` (or `str::rsplitn`) where using `str::split` would be the same.

## Examples

Example of **incorrect** code:

```rust
let str = "key=value=add";
let _ = str.splitn(3, '=').next().unwrap();
```

Example of **correct** code:

```rust
let str = "key=value=add";
let _ = str.split('=').next().unwrap();
```

## Further Reading

* [Clippy - needless_splitn](https://clippy.rust-lang.org/stable/index.html#needless_splitn)
