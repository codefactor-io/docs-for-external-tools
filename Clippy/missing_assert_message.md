Pattern: Missing message in assertion

Issue: -

## Description

Without a good custom message, it'd be hard to understand what went wrong when the assertion fails.
A good custom message should be more about why the failure of the assertion is problematic
and not what is failed because the assertion already conveys that.

Although the same reasoning applies to testing functions, this lint ignores them as they would be too noisy.
Also, in most cases understanding the test failure would be easier
compared to understanding a complex invariant distributed around the codebase.

## What it does

Checks assertions without a custom panic message.

## Examples

Example of **incorrect** code:

```rust
fn call(service: Service) {
    assert!(service.ready);
}
```

Example of **correct** code:

```rust
fn call(service: Service) {
    assert!(service.ready, "`service.poll_ready()` must be called first to ensure that service is ready to receive requests");
}
```

## Known problems

This lint cannot check the quality of the custom panic messages.
Hence, you can suppress this lint simply by adding placeholder messages
like "assertion failed". However, we recommend coming up with good messages
that provide useful information instead of placeholder messages that
don't provide any extra information.

## Further Reading

* [Clippy - missing_assert_message](https://clippy.rust-lang.org/stable/index.html#missing_assert_message)
