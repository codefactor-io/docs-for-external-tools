Pattern: Missing fields in manual `Debug` implementation

Issue: -

## Description

A common mistake is to forget to update manual `Debug` implementations when adding a new field
to a struct or a new variant to an enum.

At the same time, it also acts as a style lint to suggest using [`core::fmt::DebugStruct::finish_non_exhaustive`](https://doc.rust-lang.org/core/fmt/struct.DebugStruct.html#method.finish_non_exhaustive)
for the times when the user intentionally wants to leave out certain fields (e.g. to hide implementation details).

## What it does

Checks for manual [`core::fmt::Debug`](https://doc.rust-lang.org/core/fmt/trait.Debug.html) implementations that do not use all fields.

## Examples

Example of **incorrect** code:

```rust
use std::fmt;
struct Foo {
    data: String,
    // implementation detail
    hidden_data: i32
}
impl fmt::Debug for Foo {
    fn fmt(&self, formatter: &mut fmt::Formatter<'_>) -> fmt::Result {
        formatter
            .debug_struct("Foo")
            .field("data", &self.data)
            .finish()
    }
}
```

Example of **correct** code:

```rust
use std::fmt;
struct Foo {
    data: String,
    // implementation detail
    hidden_data: i32
}
impl fmt::Debug for Foo {
    fn fmt(&self, formatter: &mut fmt::Formatter<'_>) -> fmt::Result {
        formatter
            .debug_struct("Foo")
            .field("data", &self.data)
            .finish_non_exhaustive()
    }
}
```

## Known problems

This lint works based on the `DebugStruct` helper types provided by the `Formatter`,
so this won't detect `Debug` impls that use the `write!` macro.
Oftentimes there is more logic to a `Debug` impl if it uses `write!` macro, so it tries
to be on the conservative side and not lint in those cases in an attempt to prevent false positives.

This lint also does not look through function calls, so calling a function does not consider fields
used inside of that function as used by the `Debug` impl.

Lastly, it also ignores tuple structs as their `DebugTuple` formatter does not have a `finish_non_exhaustive`
method, as well as enums because their exhaustiveness is already checked by the compiler when matching on the enum,
making it much less likely to accidentally forget to update the `Debug` impl when adding a new variant.

## Further Reading

* [Clippy - missing_fields_in_debug](https://clippy.rust-lang.org/stable/index.html#missing_fields_in_debug)
