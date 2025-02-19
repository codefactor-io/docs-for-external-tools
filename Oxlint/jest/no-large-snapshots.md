Pattern: Large snapshot

Issue: -

## Description

Large snapshots are difficult to review and maintain. Snapshots should be kept small and focused to ensure they remain manageable and can be properly reviewed.

## Examples

Example of **incorrect** code:
```javascript
exports[`large snapshot`] = `
line 1
line 2
...
line 48
line 49
line 50
`;
```

Example of **correct** code:
```javascript
exports[`focused snapshot`] = `
<Button
  type="primary"
  onClick={handler}
>
  Submit
</Button>
`;
```