Pattern: Optional chaining with invalid undefined usage

Issue: -

## Description

Optional chaining (?.) returns undefined when the chain shorts-circuits. Using this result in contexts that don't accept undefined (like function calls, the in operator, destructuring, etc.) will cause runtime errors.

## Examples

Example of **incorrect** code:
```javascript
(obj?.foo)();  // TypeError if obj is null/undefined
let bar = 1 in obj?.foo;  // TypeError if obj is null/undefined
for (const x of obj?.foo);  // TypeError if obj is null/undefined

const { prop } = obj?.foo;  // TypeError if obj is null/undefined
const [x] = obj?.foo;  // TypeError if obj is null/undefined

with (obj?.foo);  // TypeError if obj is null/undefined
foo instanceof obj?.class;  // TypeError if obj is null/undefined
```

Example of **correct** code:
```javascript
obj?.foo?.();  // Optional call
let bar = obj?.foo && 1 in obj.foo;  // Guard with &&
for (const x of obj?.foo ?? []);  // Provide default

const { prop } = obj?.foo ?? {};  // Default for destructuring
const [x] = obj?.foo ?? [];  // Default for array destructuring

if (obj?.foo) with (obj.foo);  // Guard with if
foo instanceof (obj?.class ?? Object);  // Provide default
```