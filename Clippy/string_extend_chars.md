Pattern: Use of `extend(s.chars())` with string

Issue: -

## Description

`.push_str(s)` is clearer

## What it does

Checks for the use of `.extend(s.chars())` where s is a
`&str` or `String`.

## Examples

Example of **incorrect** code:

```rust
let abc = "abc";
let def = String::from("def");
let mut s = String::new();
s.extend(abc.chars());
s.extend(def.chars());
```

Example of **correct** code:

```rust
let abc = "abc";
let def = String::from("def");
let mut s = String::new();
s.push_str(abc);
s.push_str(&def);
```

## Further Reading

* [Clippy - string_extend_chars](https://clippy.rust-lang.org/stable/index.html#string_extend_chars)
