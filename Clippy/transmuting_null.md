Pattern: Transmute of null pointer to reference

Issue: -

## Description

Transmuting a null pointer is undefined behavior.

## What it does

Checks for transmute calls which would receive a null pointer.

## Examples

Example of **incorrect** code:

```rust
let null_ref: &u64 = unsafe { std::mem::transmute(0 as *const u64) };
```

## Known problems

Not all cases can be detected at the moment of this writing.
For example, variables which hold a null pointer and are then fed to a `transmute`
call, aren't detectable yet.

## Further Reading

* [Clippy - transmuting_null](https://clippy.rust-lang.org/stable/index.html#transmuting_null)
