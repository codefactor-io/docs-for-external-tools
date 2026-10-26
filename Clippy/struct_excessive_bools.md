Pattern: Struct with too many `bool` fields

Issue: -

## Description

Excessive bools in a struct is often a sign that
the type is being used to represent a state
machine, which is much better implemented as an
enum.

The reason an enum is better for state machines
over structs is that enums more easily forbid
invalid states.

Structs with too many booleans may benefit from refactoring
into multi variant enums for better readability and API.

## What it does

Checks for excessive
use of bools in structs.

## Examples

Example of **incorrect** code:

```rust
struct S {
    is_pending: bool,
    is_processing: bool,
    is_finished: bool,
}
```

Example of **correct** code:

```rust
enum S {
    Pending,
    Processing,
    Finished,
}
```

## Further Reading

* [Clippy - struct_excessive_bools](https://clippy.rust-lang.org/stable/index.html#struct_excessive_bools)
