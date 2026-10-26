Pattern: Use of Intel x86 assembly syntax

Issue: -

## Description

To enforce consistent use of AT&T x86 assembly syntax.

## What it does

Checks for usage of Intel x86 assembly syntax.

## Examples

Example of **incorrect** code:

```rust
asm!("lea {}, [{}]", lateout(reg) _, in(reg) ptr);
```

Example of **correct** code:

```rust
asm!("lea ({}), {}", in(reg) ptr, lateout(reg) _, options(att_syntax));
```

## Further Reading

* [Clippy - inline_asm_x86_intel_syntax](https://clippy.rust-lang.org/stable/index.html#inline_asm_x86_intel_syntax)
