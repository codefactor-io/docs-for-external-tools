Pattern: Comparison as boolean assertion

Issue: -

## Description

Using boolean assertions for numeric comparisons is less readable than Jest's built-in comparison matchers. The matchers `toBeGreaterThan`, `toBeGreaterThanOrEqual`, `toBeLessThan`, and `toBeLessThanOrEqual` should be used instead.

## Examples

Example of **incorrect** code:
```javascript
expect(x > 5).toBe(true);
expect(x < 7).not.toEqual(true);
expect(x <= y).toBe(true);
```

Example of **correct** code:
```javascript
expect(x).toBeGreaterThan(5);
expect(x).not.toBeLessThanOrEqual(7);
expect(x).toBeLessThanOrEqual(y);
```