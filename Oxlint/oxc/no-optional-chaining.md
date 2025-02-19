Pattern: Use of optional chaining

Issue: -

## Description

Optional chaining (`?.`) should be avoided when targeting older JavaScript environments as it requires verbose helper code when transpiled. Use conditional checks or logical operators instead.

## Examples

Example of **incorrect** code:
```javascript
const name = user?.profile?.name;
const result = obj.method?.();
const item = arr?.[0];
```

Example of **correct** code:
```javascript
const name = user && user.profile && user.profile.name;
const result = obj.method && obj.method();
const item = arr && arr[0];
```