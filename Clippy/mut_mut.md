Pattern: Use of `&mut &mut` reference

Issue: -

## Description

This is usually just a typo or a misunderstanding of how references work.

## What it does

Checks for instances of `mut mut` references.

## Examples

Example of **incorrect** code:

```rust
let x = &mut &mut 1;

let mut x = &mut 1;
let y = &mut x;

fn foo(x: &mut &mut u32) {}
```

Example of **correct** code:

```rust
let x = &mut 1;

let mut x = &mut 1;
let y = &mut *x; // reborrow

fn foo(x: &mut u32) {}
```

## Further Reading

* [Clippy - mut_mut](https://clippy.rust-lang.org/stable/index.html#mut_mut)
