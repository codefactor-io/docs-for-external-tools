Pattern: Redundant `test_` prefix in test name

Issue: -

## Description

This is redundant because test functions are already annotated with `#[test]`.
Moreover, it clutters the output of `cargo test` since test functions are expanded as
`module::tests::test_use_case` in the output. Without the redundant prefix, the output
becomes `module::tests::use_case`, which is more readable.

## What it does

Checks for test functions (functions annotated with `#[test]`) that are prefixed
with `test_` which is redundant.

## Examples

Example of **incorrect** code:

```rust
#[cfg(test)]
mod tests {
  use super::*;

  #[test]
  fn test_use_case() {
      // test code
  }
}
```

Example of **correct** code:

```rust
#[cfg(test)]
mod tests {
  use super::*;

  #[test]
  fn use_case() {
      // test code
  }
}
```

## Note

Clippy can only lint compiled code. For this lint to trigger, you must configure `cargo clippy`
to include test compilation, for instance, by using flags such as `--tests` or `--all-targets`.

## Further Reading

* [Clippy - redundant_test_prefix](https://clippy.rust-lang.org/stable/index.html#redundant_test_prefix)
