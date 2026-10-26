Pattern: Items out of configured order

Issue: -

## Description

Keeping a consistent ordering throughout the codebase helps with working
as a team, and possibly improves maintainability of the codebase. The
idea is that by defining a consistent and enforceable rule for how
source files are structured, less time will be wasted during reviews on
a topic that is (under most circumstances) not relevant to the logic
implemented in the code. Sometimes this will be referred to as
"bikeshedding".

The content of items with a representation clause attribute, such as
`#[repr(C)]` will not be checked, as the order of their fields or
variants might be dictated by an external API (application binary
interface).

## What it does

Confirms that items are sorted in source files as per configuration.

## Examples

```rust
trait TraitUnordered {
    const A: bool;
    const C: bool;
    const B: bool;

    type SomeType;

    fn a();
    fn c();
    fn b();
}
```

Use instead:
```rust
trait TraitOrdered {
    const A: bool;
    const B: bool;
    const C: bool;

    type SomeType;

    fn a();
    fn b();
    fn c();
}
```

[cargo-pgo]: https://github.com/Kobzol/cargo-pgo/blob/main/README.md

## Default Ordering and Configuration

As there is no generally applicable rule, and each project may have
different requirements, the lint can be configured with high
granularity. The configuration is split into two stages:

1. Which item kinds that should have an internal order enforced.
2. Individual ordering rules per item kind.

The item kinds that can be linted are:
- Module (with customized groupings, alphabetical within - configurable)
- Trait (with customized order of associated items, alphabetical within)
- Enum, Impl, Struct (purely alphabetical)

#### Module Item Order

Due to the large variation of items within modules, the ordering can be
configured on a very granular level. Item kinds can be grouped together
arbitrarily, items within groups will be ordered alphabetically. The
following table shows the default groupings:

| Group              | Item Kinds           |
|--------------------|----------------------|
| `modules`          | "mod", "foreign_mod" |
| `use`              | "use"                |
| `macros`           | "macro"              |
| `global_asm`       | "global_asm"         |
| `UPPER_SNAKE_CASE` | "static", "const"    |
| `PascalCase`       | "ty_alias", "opaque_ty", "enum", "struct", "union", "trait", "trait_alias", "impl" |
| `lower_snake_case` | "fn"                 |

The groups' names are arbitrary and can be changed to suit the
conventions that should be enforced for a specific project.

All item kinds must be accounted for to create an enforceable linting
rule set. Following are some example configurations that may be useful.

Example: *module inclusions and use statements to be at the top*

```toml
module-item-order-groupings = [
    [ "modules", [ "extern_crate", "mod", "foreign_mod" ], ],
    [ "use", [ "use", ], ],
    [ "everything_else", [ "macro", "global_asm", "static", "const", "ty_alias", "enum", "struct", "union", "trait", "trait_alias", "impl", "fn", ], ],
]
```

Example: *only consts and statics should be alphabetically ordered*

It is also possible to configure a selection of module item groups that
should be ordered alphabetically. This may be useful if for example
statics and consts should be ordered, but the rest should be left open.

```toml
module-items-ordered-within-groupings = ["UPPER_SNAKE_CASE"]
```

## Known Problems

#### Performance Impact

Keep in mind, that ordering source code alphabetically can lead to
reduced performance in cases where the most commonly used enum variant
isn't the first entry anymore, and similar optimizations that can reduce
branch misses, cache locality and such. Either don't use this lint if
that's relevant, or disable the lint in modules or items specifically
where it matters. Other solutions can be to use profile guided
optimization (PGO), post-link optimization (e.g. using BOLT for LLVM),
or other advanced optimization methods. A good starting point to dig
into optimization is [cargo-pgo][cargo-pgo].

#### Lints on a Contains basis

The lint can be disabled only on a "contains" basis, but not per element
within a "container", e.g. the lint works per-module, per-struct,
per-enum, etc. but not for "don't order this particular enum variant".

#### Module documentation

Module level rustdoc comments are not part of the resulting syntax tree
and as such cannot be linted from within `check_mod`. Instead, the
`rustdoc::missing_documentation` lint may be used.

#### Module Tests

This lint does not implement detection of module tests (or other feature
dependent elements for that matter). To lint the location of mod tests,
the lint `items_after_test_module` can be used instead.

## Further Reading

* [Clippy - arbitrary_source_item_ordering](https://clippy.rust-lang.org/stable/index.html#arbitrary_source_item_ordering)
