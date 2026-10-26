Pattern: Test function outside test module

Issue: -

## Description

The idiomatic (and more performant) way of writing tests is inside a testing module (flagged with `#[cfg(test)]`),
having test functions outside of this module is confusing and may lead to them being "hidden".

## What it does

Triggers when a testing function (marked with the `#[test]` attribute) isn't inside a testing module
(marked with `#[cfg(test)]`).

## Examples

Example of **incorrect** code:

```rust
#[test]
fn my_cool_test() {
    // [...]
}

#[cfg(test)]
mod tests {
    // [...]
}

```

Example of **correct** code:

```rust
#[cfg(test)]
mod tests {
    #[test]
    fn my_cool_test() {
        // [...]
    }
}
```

## Further Reading

* [Clippy - tests_outside_test_module](https://clippy.rust-lang.org/stable/index.html#tests_outside_test_module)
