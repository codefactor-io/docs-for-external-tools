Pattern: Disallowed type held across `await`

Issue: -

## Description

There are some types which are perfectly safe to use concurrently from
a memory access perspective, but that will cause bugs at runtime if
they are held in such a way.

## What it does

Allows users to configure types which should not be held across await
suspension points.

## Examples

```toml
await-holding-invalid-types = [
  # You can specify a type name
  "CustomLockType",
  # You can (optionally) specify a reason
  { path = "OtherCustomLockType", reason = "Relies on a thread local" }
]
```

```rust
struct CustomLockType;
struct OtherCustomLockType;
async fn foo() {
  let _x = CustomLockType;
  let _y = OtherCustomLockType;
  baz().await; // Lint violation
}
```

## Further Reading

* [Clippy - await_holding_invalid_type](https://clippy.rust-lang.org/stable/index.html#await_holding_invalid_type)
