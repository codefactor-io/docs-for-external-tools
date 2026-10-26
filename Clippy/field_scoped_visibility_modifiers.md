Pattern: Scoped visibility modifier on field

Issue: -

## Description

Scoped visibility modifiers cause a field to be accessible within some scope between
public and private, potentially within an entire crate. This allows for fields to be
non-private while upholding internal invariants, but can be a code smell. Scoped visibility
requires checking a greater area, potentially an entire crate, to verify that an invariant
is upheld, and global analysis requires a lot of effort.

## What it does

Checks for usage of scoped visibility modifiers, like `pub(crate)`, on fields. These
make a field visible within a scope between public and private.

## Examples

Example of **incorrect** code:

```rust
pub mod public_module {
    struct MyStruct {
        pub(crate) first_field: bool,
        pub(super) second_field: bool
    }
}
```

Example of **correct** code:

```rust
pub mod public_module {
    struct MyStruct {
        first_field: bool,
        second_field: bool
    }
    impl MyStruct {
        pub(crate) fn get_first_field(&self) -> bool {
            self.first_field
        }
        pub(super) fn get_second_field(&self) -> bool {
            self.second_field
        }
    }
}
```

## Further Reading

* [Clippy - field_scoped_visibility_modifiers](https://clippy.rust-lang.org/stable/index.html#field_scoped_visibility_modifiers)
