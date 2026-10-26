Pattern: Wrong `self` convention for method name

Issue: -

## Description

Consistency breeds readability. If you follow the
conventions, your users won't be surprised that they, e.g., need to supply a
mutable reference to a `as_..` function.

## What it does

Checks for methods with certain name prefixes or suffixes, and which
do not adhere to standard conventions regarding how `self` is taken.
The actual rules are:

|Prefix |Postfix     |`self` taken                   | `self` type  |
|-------|------------|-------------------------------|--------------|
|`as_`  | none       |`&self` or `&mut self`         | any          |
|`from_`| none       | none                          | any          |
|`into_`| none       |`self`                         | any          |
|`is_`  | none       |`&mut self` or `&self` or none | any          |
|`to_`  | `_mut`     |`&mut self`                    | any          |
|`to_`  | not `_mut` |`self`                         | `Copy`       |
|`to_`  | not `_mut` |`&self`                        | not `Copy`   |

Note: Clippy doesn't trigger methods with `to_` prefix in:
- Traits definition.
Clippy can not tell if a type that implements a trait is `Copy` or not.
- Traits implementation, when `&self` is taken.
The method signature is controlled by the trait and often `&self` is required for all types that implement the trait
(see e.g. the `std::string::ToString` trait).

Clippy allows `Pin<&Self>` and `Pin<&mut Self>` if `&self` and `&mut self` is required.

Please find more info here:
https://rust-lang.github.io/api-guidelines/naming.html#ad-hoc-conversions-follow-as_-to_-into_-conventions-c-conv

## Examples

Example of **incorrect** code:

```rust
impl X {
    fn as_str(self) -> &'static str {
        // ..
    }
}
```

Example of **correct** code:

```rust
impl X {
    fn as_str(&self) -> &'static str {
        // ..
    }
}
```

## Further Reading

* [Clippy - wrong_self_convention](https://clippy.rust-lang.org/stable/index.html#wrong_self_convention)
