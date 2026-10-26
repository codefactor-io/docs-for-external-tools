Pattern: Implementation of `Into` instead of `From`

Issue: -

## Description

According the std docs implementing `From<..>` is preferred since it gives you `Into<..>` for free where the reverse isn't true.

## What it does

Searches for implementations of the `Into<..>` trait and suggests to implement `From<..>` instead.

## Examples

Example of **incorrect** code:

```rust
struct StringWrapper(String);

impl Into<StringWrapper> for String {
    fn into(self) -> StringWrapper {
        StringWrapper(self)
    }
}
```

Example of **correct** code:

```rust
struct StringWrapper(String);

impl From<String> for StringWrapper {
    fn from(s: String) -> StringWrapper {
        StringWrapper(s)
    }
}
```

## Further Reading

* [Clippy - from_over_into](https://clippy.rust-lang.org/stable/index.html#from_over_into)
