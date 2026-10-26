Pattern: Consecutive `str::replace()` calls

Issue: -

## Description

Consecutive `str::replace` calls scan the string multiple times
with repetitive code.

## What it does

Checks for consecutive calls to `str::replace` (2 or more)
that can be collapsed into a single call.

## Examples

Example of **incorrect** code:

```rust
let hello = "hesuo worpd"
    .replace('s', "l")
    .replace("u", "l")
    .replace('p', "l");
```

Example of **correct** code:

```rust
let hello = "hesuo worpd".replace(['s', 'u', 'p'], "l");
```

## Further Reading

* [Clippy - collapsible_str_replace](https://clippy.rust-lang.org/stable/index.html#collapsible_str_replace)
