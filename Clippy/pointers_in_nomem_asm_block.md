Pattern: Pointer passed to `nomem` `asm!` block

Issue: -

## Description

`nomem` forbids any reads or writes to memory and passing a pointer suggests
that either of those will happen.

## What it does

Checks if any pointer is being passed to an asm! block with `nomem` option.

## Examples

Example of **incorrect** code:

```rust
fn f(p: *mut u32) {
    unsafe { core::arch::asm!("mov [{p}], 42", p = in(reg) p, options(nomem, nostack)); }
}
```

Example of **correct** code:

```rust
fn f(p: *mut u32) {
    unsafe { core::arch::asm!("mov [{p}], 42", p = in(reg) p, options(nostack)); }
}
```

## Further Reading

* [Clippy - pointers_in_nomem_asm_block](https://clippy.rust-lang.org/stable/index.html#pointers_in_nomem_asm_block)
