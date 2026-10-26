Pattern: Unnecessary `&*` on reference

Issue: -

## Description

Dereferencing and then borrowing a reference value has no effect in most cases.

## What it does

Checks for `&*(&T)`.

## Examples

Example of **incorrect** code:

```rust
let s = &String::new();

let a: &String = &* s;
```

Example of **correct** code:

```rust
let a: &String = s;
```

## Known problems

False negative on such code:
```rust
let x = &12;
let addr_x = &x as *const _ as usize;
let addr_y = &&*x as *const _ as usize; // assert ok now, and lint triggered.
                                        // But if we fix it, assert will fail.
assert_ne!(addr_x, addr_y);
```

## Further Reading

* [Clippy - borrow_deref_ref](https://clippy.rust-lang.org/stable/index.html#borrow_deref_ref)
