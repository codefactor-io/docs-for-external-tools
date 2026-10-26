Pattern: `to_owned()` on `Cow`

Issue: -

## Description

Calling `to_owned()` on a `Cow` creates a clone of the `Cow`
itself, without taking ownership of the `Cow` contents (i.e.
it's equivalent to calling `Cow::clone`).
The similarly named `into_owned` method, on the other hand,
clones the `Cow` contents, effectively turning any `Cow::Borrowed`
into a `Cow::Owned`.

Given the potential ambiguity, consider replacing `to_owned`
with `clone` for better readability or, if getting a `Cow::Owned`
was the original intent, using `into_owned` instead.

## What it does

Checks for the usage of `_.to_owned()`, on a `Cow<'_, _>`.

## Examples

```rust
let s = "Hello world!";
let cow = Cow::Borrowed(s);

let data = cow.to_owned();
assert!(matches!(data, Cow::Borrowed(_)))
```
Use instead:
```rust
let s = "Hello world!";
let cow = Cow::Borrowed(s);

let data = cow.clone();
assert!(matches!(data, Cow::Borrowed(_)))
```
or
```rust
let s = "Hello world!";
let cow = Cow::Borrowed(s);

let _data: String = cow.into_owned();
```

## Further Reading

* [Clippy - suspicious_to_owned](https://clippy.rust-lang.org/stable/index.html#suspicious_to_owned)
