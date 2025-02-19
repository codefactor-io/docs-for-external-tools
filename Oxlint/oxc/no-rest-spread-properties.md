Pattern: Use of object rest/spread

Issue: -

## Description

Object rest/spread syntax should be avoided when targeting environments that don't support this feature. Use alternative methods like `Object.assign` for object spreading and manual property assignments for rest properties.

## Examples

Example of **incorrect** code:
```javascript
const obj = { ...source };
const { a, ...rest } = data;
let newObj = { x, y, ...z };
```

Example of **correct** code:
```javascript
const obj = Object.assign({}, source);
const a = data.a;
const rest = Object.assign({}, data);
delete rest.a;
```