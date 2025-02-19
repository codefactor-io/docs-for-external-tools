Pattern: Spread in `map` callback

Issue: -

## Description

Using spread operators in `Array.prototype.map` callbacks to add properties creates unnecessary object allocations. Use `Object.assign` instead for better performance when mutation is acceptable.

## Examples

Example of **incorrect** code:
```javascript
const enhanced = items.map(item => ({
  ...item,
  timestamp: Date.now()
}));

const combined = data.map(d => ({
  ...d,
  ...extraData
}));
```

Example of **correct** code:
```javascript
const enhanced = items.map(item => 
  Object.assign(item, { timestamp: Date.now() })
);

// If you need to prevent mutations
const enhanced = items.map(item => 
  Object.assign({}, item, { timestamp: Date.now() })
);
```