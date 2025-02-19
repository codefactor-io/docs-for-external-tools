Pattern: Use of `process.exit()`

Issue: -

## Description

The `process.exit()` method should only be used in command-line applications. In other contexts, throwing an error provides better error handling and stack traces.

## Examples

Example of **incorrect** code:
```javascript
if (problem) process.exit(1);
```

Example of **correct** code:
```javascript
if (problem) throw new Error("message");

// In CLI apps:
#!/usr/bin/env node
if (problem) process.exit(1);
```