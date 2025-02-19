Pattern: Unsorted variable declarations

Issue: -

## Description

When declaring multiple variables in a single statement, sorting variable names alphabetically makes it easier to scan the list and find specific variables. This improves code readability and helps identify duplicates.

## Examples

Example of **incorrect** code:
```javascript
var z, x, y;
var d, a, c, b;

const {foo, bar, baz} = obj;
let [second, first] = array;

var test, 
    app,
    init;
```

Example of **correct** code:
```javascript
var x, y, z;
var a, b, c, d;

const {bar, baz, foo} = obj;
let [first, second] = array;

var app,
    init,
    test;
```