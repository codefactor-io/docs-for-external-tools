Pattern: Missing use of IP address constant

Issue: -

## Description

Using specific IP addresses like `127.0.0.1` or `::1` is less clear and less maintainable than using the
predefined constants `Ipv4Addr::LOCALHOST` or `Ipv6Addr::LOCALHOST`. These constants improve code
readability, make the intent explicit, and are less error-prone.

## What it does

Checks for IP addresses that could be replaced with predefined constants such as
`Ipv4Addr::new(127, 0, 0, 1)` instead of using the appropriate constants.

## Examples

Example of **incorrect** code:

```rust
use std::net::{Ipv4Addr, Ipv6Addr};

// IPv4 loopback
let addr_v4 = Ipv4Addr::new(127, 0, 0, 1);

// IPv6 loopback
let addr_v6 = Ipv6Addr::new(0, 0, 0, 0, 0, 0, 0, 1);
```

Example of **correct** code:

```rust
use std::net::{Ipv4Addr, Ipv6Addr};

// IPv4 loopback
let addr_v4 = Ipv4Addr::LOCALHOST;

// IPv6 loopback
let addr_v6 = Ipv6Addr::LOCALHOST;
```

## Further Reading

* [Clippy - ip_constant](https://clippy.rust-lang.org/stable/index.html#ip_constant)
