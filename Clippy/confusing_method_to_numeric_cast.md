Pattern: Cast of primitive method to integer

Issue: -

## Description

Casting a function pointer to an integer can have surprising results and can occur
accidentally if parentheses are omitted from a function call. If you aren't doing anything
low-level with function pointers then you can opt out of casting functions to integers in
order to avoid mistakes. Alternatively, you can use this lint to audit all uses of function
pointer casts in your code.

## What it does

Checks for casts of a primitive method pointer like `max`/`min` to any integer type.

## Examples

Example of **incorrect** code:

```rust
let _ = u16::max as usize;
```

Example of **correct** code:

```rust
let _ = u16::MAX as usize;
```

## Further Reading

* [Clippy - confusing_method_to_numeric_cast](https://clippy.rust-lang.org/stable/index.html#confusing_method_to_numeric_cast)
