Pattern: Unused `new` operator expression

Issue: -

## Description

Using `new` without storing or comparing the resulting object reference throws away the created instance. This is usually a mistake, as constructor side effects should be handled by regular functions instead.

## Examples

Example of **incorrect** code:
```javascript
new Person();

function init() {
  new Config();  // Instance is discarded
}

new Object();
```

Example of **correct** code:
```javascript
const person = new Person();

let user;
if (condition) {
  user = new Person();
}

const config = new Config();
initialize(config);

// Use function for side effects
initialize();
```