Pattern: Global objects called as functions

Issue: -

## Description

Some global objects (Math, JSON, Reflect, Atomics, Intl) are not intended to be used as functions or constructors. Calling them as functions or with `new` will result in a TypeError. Use their static methods instead.

## Examples

Example of **incorrect** code:
```javascript
const math = Math();
const json = JSON();
const reflect = Reflect();
const atomics = new Atomics();
const intl = Intl();

const newMath = new Math();
const newJSON = new JSON();
```

Example of **correct** code:
```javascript
const area = Math.PI * r * r;
const obj = JSON.parse("{}");
const value = Reflect.get(obj, "prop");
const result = Atomics.add(shared, 0, 1);
const formatter = new Intl.DateTimeFormat("en-US");
```