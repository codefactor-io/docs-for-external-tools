Pattern: Unsecure URL scheme

Issue: -

## Description

Checks for usage of potentially unsecure URL schemes (`http`, `ws`) in string literals. Using unencrypted URL schemes can expose sensitive data during transmission and make applications vulnerable to man-in-the-middle attacks. Secure alternatives like `https` should be preferred when possible.


## Further Reading

* [Revive - unsecure-url-scheme](https://revive.run/r#unsecure-url-scheme)