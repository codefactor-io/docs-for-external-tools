Pattern: Empty destructuring pattern

Issue: -

## Description

Empty destructuring patterns ({} or []) have no effect and are usually a mistake. Often, developers intended to use a default value assignment (= {}) instead of an empty pattern, or forgot to specify the properties to destructure.

## Examples

Example of **incorrect** code:
```javascript
var {} = foo;
var [] = foo;
var {a: {}} = foo;
var {a: []} = foo;

function foo({}) {}
function bar([]) {}
function baz({a: {}}) {}
```

Example of **correct** code:
```javascript
var {a = {}} = foo;
var [a = []] = foo;
var {a: {b}} = foo;
var {a: [x]} = foo;

function foo({a = {}}) {}
function bar([a = []]) {}
function baz({a: {b}}) {}
```