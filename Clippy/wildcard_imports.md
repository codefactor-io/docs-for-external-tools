Pattern: Wildcard import

Issue: -

## Description

wildcard imports can pollute the namespace. This is especially bad if
you try to import something through a wildcard, that already has been imported by name from
a different source:

```rust
use crate1::foo; // Imports a function named foo
use crate2::*; // Has a function named foo

foo(); // Calls crate1::foo
```

This can lead to confusing error messages at best and to unexpected behavior at worst.

## What it does

Checks for wildcard imports `use _::*`.

## Examples

Example of **incorrect** code:

```rust
use crate1::*;

foo();
```

Example of **correct** code:

```rust
use crate1::foo;

foo();
```

## Exceptions

Wildcard imports are allowed from modules that their name contains `prelude`. Many crates
(including the standard library) provide modules named "prelude" specifically designed
for wildcard import.

Wildcard imports reexported through `pub use` are also allowed.

`use super::*` is allowed in test modules. This is defined as any module with "test" in the name.

These exceptions can be disabled using the `warn-on-all-wildcard-imports` configuration flag.

## Known problems

If macros are imported through the wildcard, this macro is not included
by the suggestion and has to be added by hand.

Applying the suggestion when explicit imports of the things imported with a glob import
exist, may result in `unused_imports` warnings.

## Further Reading

* [Clippy - wildcard_imports](https://clippy.rust-lang.org/stable/index.html#wildcard_imports)
