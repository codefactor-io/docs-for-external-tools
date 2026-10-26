Pattern: `SAFETY` comment on safe code

Issue: -

## Description

Safe code has no safety requirements, so there is no need to
describe safety invariants.

## What it does

Checks for `// SAFETY: ` comments on safe code.

## Examples

Example of **incorrect** code:

```rust
use std::ptr::NonNull;
let a = &mut 42;

// SAFETY: references are guaranteed to be non-null.
let ptr = NonNull::new(a).unwrap();
```

Example of **correct** code:

```rust
use std::ptr::NonNull;
let a = &mut 42;

let ptr = NonNull::new(a).unwrap();
```

## Further Reading

* [Clippy - unnecessary_safety_comment](https://clippy.rust-lang.org/stable/index.html#unnecessary_safety_comment)
