Pattern: Symbol without description

Issue: -

## Description

Symbols should include a description to make debugging easier. When a Symbol is logged, its description appears in the output, making it easier to identify different Symbols and their purposes.

## Examples

Example of **incorrect** code:
```javascript
const sym1 = Symbol();
const sym2 = Symbol();
let id = Symbol();

const toPrimitive = Symbol();
obj[Symbol()] = 'value';
```

Example of **correct** code:
```javascript
const sym1 = Symbol('sym1');
const sym2 = Symbol('unique key');
let id = Symbol('id');

const toPrimitive = Symbol('Symbol.toPrimitive');
const desc = 'my symbol';
obj[Symbol(desc)] = 'value';
```