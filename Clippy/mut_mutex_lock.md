Pattern: Unnecessary `Mutex::lock()` on `&mut Mutex`

Issue: -

## Description

`Mutex::lock` is less efficient than
calling `Mutex::get_mut`. In addition you also have a statically
guarantee that the mutex isn't locked, instead of just a runtime
guarantee.

## What it does

Checks for `&mut Mutex::lock` calls

## Examples

Example of **incorrect** code:

```rust
use std::sync::{Arc, Mutex};

let mut value_rc = Arc::new(Mutex::new(42_u8));
let value_mutex = Arc::get_mut(&mut value_rc).unwrap();

let mut value = value_mutex.lock().unwrap();
*value += 1;
```

Example of **correct** code:

```rust
use std::sync::{Arc, Mutex};

let mut value_rc = Arc::new(Mutex::new(42_u8));
let value_mutex = Arc::get_mut(&mut value_rc).unwrap();

let value = value_mutex.get_mut().unwrap();
*value += 1;
```

## Further Reading

* [Clippy - mut_mutex_lock](https://clippy.rust-lang.org/stable/index.html#mut_mutex_lock)
