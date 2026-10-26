Pattern: Item name repeats module name

Issue: -

## Description

It requires the user to type the module name twice in each usage,
especially if they choose to import the module rather than its contents.

Lack of such repetition is also the style used in the Rust standard library;
e.g. `io::Error` and `fmt::Error` rather than `io::IoError` and `fmt::FmtError`;
and `array::from_ref` rather than `array::array_from_ref`.

## What it does

Detects public item names that are prefixed or suffixed by the
containing public module's name.

## Examples

Example of **incorrect** code:

```rust
mod cake {
    struct BlackForestCake;
}
```

Example of **correct** code:

```rust
mod cake {
    struct BlackForest;
}
```

## Known issues

Glob re-exports are ignored; e.g. this will not warn even though it should:

```rust
pub mod foo {
    mod iteration {
        pub struct FooIter {}
    }
    pub use iteration::*; // creates the path `foo::FooIter`
}
```

## Further Reading

* [Clippy - module_name_repetitions](https://clippy.rust-lang.org/stable/index.html#module_name_repetitions)
