Pattern: Use of `console` method

Issue: -

## Description

In browser-targeted JavaScript, `console` methods are primarily meant for debugging and should not be shipped to production. Use proper logging services or custom error handling mechanisms instead.

## Examples

Example of **incorrect** code:
```javascript
console.log("User logged in");
console.error("Failed to load resource");
console.warn("Deprecated feature used");
```

Example of **correct** code:
```javascript
logger.info("User logged in");
errorHandler.report("Failed to load resource");
metrics.warn("Deprecated feature used");
```