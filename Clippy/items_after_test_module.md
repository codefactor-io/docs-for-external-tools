Pattern: Item after test module

Issue: -

## Description

Having items declared after the testing module is confusing and may lead to bad test coverage.

## What it does

Triggers if an item is declared after the testing module marked with `#[cfg(test)]`.

## Examples

Example of **incorrect** code:

```rust
#[cfg(test)]
mod tests {
    // [...]
}

fn my_function() {
    // [...]
}
```

Example of **correct** code:

```rust
fn my_function() {
    // [...]
}

#[cfg(test)]
mod tests {
    // [...]
}
```

## Further Reading

* [Clippy - items_after_test_module](https://clippy.rust-lang.org/stable/index.html#items_after_test_module)
