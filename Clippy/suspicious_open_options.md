Pattern: `OpenOptions::create()` without `truncate()`

Issue: -

## Description

`create()` alone will either create a new file or open an
existing file. If the file already exists, it will be
overwritten when written to, but the file will not be
truncated by default.
If less data is written to the file
than it already contains, the remainder of the file will
remain unchanged, and the end of the file will contain old
data.
In most cases, one should either use `create_new` to ensure
the file is created from scratch, or ensure `truncate` is
called so that the truncation behaviour is explicit. `truncate(true)`
will ensure the file is entirely overwritten with new data, whereas
`truncate(false)` will explicitly keep the default behavior.

## What it does

Checks for the suspicious use of `OpenOptions::create()`
without an explicit `OpenOptions::truncate()`.

## Examples

Example of **incorrect** code:

```rust
use std::fs::OpenOptions;

OpenOptions::new().create(true);
```

Example of **correct** code:

```rust
use std::fs::OpenOptions;

OpenOptions::new().create(true).truncate(true);
```

## Further Reading

* [Clippy - suspicious_open_options](https://clippy.rust-lang.org/stable/index.html#suspicious_open_options)
