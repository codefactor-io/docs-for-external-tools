Pattern: Missing use of `assert!`

Issue: -

## Description

`assert!` is simpler than `if`-then-`panic!`.

## What it does

Detects `if`-then-`panic!` that can be replaced with `assert!`.

## Examples

Example of **incorrect** code:

```rust
let sad_people: Vec<&str> = vec![];
if !sad_people.is_empty() {
    panic!("there are sad people: {:?}", sad_people);
}
```

Example of **correct** code:

```rust
let sad_people: Vec<&str> = vec![];
assert!(sad_people.is_empty(), "there are sad people: {:?}", sad_people);
```

## Further Reading

* [Clippy - manual_assert](https://clippy.rust-lang.org/stable/index.html#manual_assert)
