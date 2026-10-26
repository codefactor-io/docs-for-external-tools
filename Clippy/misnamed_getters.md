Pattern: Getter returning wrong field

Issue: -

## Description

It is most likely that such a method is a bug caused by a typo or by copy-pasting.

## What it does

Checks for getter methods that return a field that doesn't correspond
to the name of the method, when there is a field's whose name matches that of the method.

## Examples

Example of **incorrect** code:

```rust
struct A {
    a: String,
    b: String,
}

impl A {
    fn a(&self) -> &str{
        &self.b
    }
}
```

Example of **correct** code:

```rust
struct A {
    a: String,
    b: String,
}

impl A {
    fn a(&self) -> &str{
        &self.a
    }
}
```

## Further Reading

* [Clippy - misnamed_getters](https://clippy.rust-lang.org/stable/index.html#misnamed_getters)
