Pattern: Unnecessary `::{self}` import

Issue: -

## Description

In most cases, this can be written much more cleanly by omitting `::{self}`.

## What it does

Checks for imports ending in `::{self}`.

## Examples

Example of **incorrect** code:

```rust
use std::io::{self};
```

Example of **correct** code:

```rust
use std::io;
```

## Known problems

Removing `::{self}` will cause any non-module items at the same path to also be imported.
This might cause a naming conflict (https://github.com/rust-lang/rustfmt/issues/3568). This lint makes no attempt
to detect this scenario and that is why it is a restriction lint.

## Further Reading

* [Clippy - unnecessary_self_imports](https://clippy.rust-lang.org/stable/index.html#unnecessary_self_imports)
