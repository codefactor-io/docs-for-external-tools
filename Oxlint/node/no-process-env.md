Pattern: Use of `process.env`

Issue: -

## Description

Directly reading `process.env` can lead to implicit runtime configuration,
make code harder to test, and bypass configuration validation.

## Examples

Example of **incorrect** code:
```javascript
if (process.env.NODE_ENV === "development") {
  // ...
}
```

Example of **correct** code:
```javascript
import config from "./config";

if (config.env === "development") {
  //...
}
```
