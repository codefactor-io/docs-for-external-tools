Pattern: `#[repr(packed)]` without ABI

Issue: -

## Description

Without qualification, `repr(packed)` implies `repr(Rust)`. The Rust-ABI is inherently unstable.
While this is fine as long as the type is accessed correctly within Rust-code, most uses
of `#[repr(packed)]` involve FFI and/or data structures specified by network-protocols or
other external specifications. In such situations, the unstable Rust-ABI implied in
`#[repr(packed)]` may lead to future bugs should the Rust-ABI change.

In case you are relying on a well defined and stable memory layout, qualify the type's
representation using the `C`-ABI. Otherwise, if the type in question is only ever
accessed from Rust-code according to Rust's rules, use the `Rust`-ABI explicitly.

## What it does

Checks for items with `#[repr(packed)]`-attribute without ABI qualification

## Examples

Example of **incorrect** code:

```rust
#[repr(packed)]
struct NetworkPacketHeader {
    header_length: u8,
    header_version: u16
}
```

Example of **correct** code:

```rust
#[repr(C, packed)]
struct NetworkPacketHeader {
    header_length: u8,
    header_version: u16
}
```

## Further Reading

* [Clippy - repr_packed_without_abi](https://clippy.rust-lang.org/stable/index.html#repr_packed_without_abi)
