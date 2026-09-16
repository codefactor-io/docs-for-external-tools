Pattern: Async wrapper instead of top-level await

Issue: -

## Description

Top-level await is more readable and can prevent unhandled rejections.

## Examples

Example of **incorrect** code:
```javascript
(async () => {
  await run();
})();

run().catch((error) => {
  console.error(error);
});
```

Example of **correct** code:
```javascript
await run();

try {
  await run();
} catch (error) {
  console.error(error);
}
```
