Pattern: Enum with no variants

Issue: -

## Description

* If you only want a type which can’t be instantiated, you should use [`!`]
  (the primitive type "never"), because [`!`] has more extensive compiler support
  (type inference, etc.) and implementations of common traits.

* If you need to introduce a distinct type, consider using a [newtype] `struct`
  containing [`!`] instead (`struct MyType(pub !)`), because it is more idiomatic
  to use a `struct` rather than an `enum` when an `enum` is unnecessary.

  If you do this, note that the [visibility] of the [`!`] field determines whether
  the uninhabitedness is visible in documentation, and whether it can be pattern
  matched to mark code unreachable. If the field is not visible, then the struct
  acts like any other struct with private fields.

For further information, visit
[the never type’s documentation][`!`].

## What it does

Checks for `enum`s with no variants, which therefore are uninhabited types
(cannot be instantiated).

As of this writing, the `never_type` is still a nightly-only experimental API.
Therefore, this lint is only triggered if `#![feature(never_type)]` is enabled.

## Examples

```rust
enum CannotExist {}
```

Use instead:
```rust
#![feature(never_type)]

/// Use the `!` type directly...
type CannotExist = !;

/// ...or define a newtype which is distinct.
struct CannotExist2(pub !);
```

[`!`]: https://doc.rust-lang.org/std/primitive.never.html
[cfg]: https://doc.rust-lang.org/reference/conditional-compilation.html
[newtype]: https://doc.rust-lang.org/book/ch19-04-advanced-types.html#using-the-newtype-pattern-for-type-safety-and-abstraction
[visibility]: https://doc.rust-lang.org/reference/visibility-and-privacy.html

## Further Reading

* [Clippy - empty_enums](https://clippy.rust-lang.org/stable/index.html#empty_enums)
