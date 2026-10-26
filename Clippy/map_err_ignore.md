Pattern: Use of `map_err()` that discards original error

Issue: -

## Description

This `map_err` throws away the original error rather than allowing the enum to
contain and report the cause of the error.

## What it does

Checks for instances of `map_err(|_| Some::Enum)`

## Examples

Before:
```rust
use std::fmt;

#[derive(Debug)]
enum Error {
    Indivisible,
    Remainder(u8),
}

impl fmt::Display for Error {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        match self {
            Error::Indivisible => write!(f, "could not divide input by three"),
            Error::Remainder(remainder) => write!(
                f,
                "input is not divisible by three, remainder = {}",
                remainder
            ),
        }
    }
}

impl std::error::Error for Error {}

fn divisible_by_3(input: &str) -> Result<(), Error> {
    input
        .parse::<i32>()
        .map_err(|_| Error::Indivisible)
        .map(|v| v % 3)
        .and_then(|remainder| {
            if remainder == 0 {
                Ok(())
            } else {
                Err(Error::Remainder(remainder as u8))
            }
        })
}
```

After:
```rust
use std::{fmt, num::ParseIntError};

#[derive(Debug)]
enum Error {
    Indivisible(ParseIntError),
    Remainder(u8),
}

impl fmt::Display for Error {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        match self {
            Error::Indivisible(_) => write!(f, "could not divide input by three"),
            Error::Remainder(remainder) => write!(
                f,
                "input is not divisible by three, remainder = {}",
                remainder
            ),
        }
    }
}

impl std::error::Error for Error {
    fn source(&self) -> Option<&(dyn std::error::Error + 'static)> {
        match self {
            Error::Indivisible(source) => Some(source),
            _ => None,
        }
    }
}

fn divisible_by_3(input: &str) -> Result<(), Error> {
    input
        .parse::<i32>()
        .map_err(Error::Indivisible)
        .map(|v| v % 3)
        .and_then(|remainder| {
            if remainder == 0 {
                Ok(())
            } else {
                Err(Error::Remainder(remainder as u8))
            }
        })
}
```

## Further Reading

* [Clippy - map_err_ignore](https://clippy.rust-lang.org/stable/index.html#map_err_ignore)
