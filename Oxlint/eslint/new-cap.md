Pattern: Constructor function without capital letter

Issue: -

## Description

Constructor functions create new instances of objects when called with the `new` operator. By convention, constructor functions begin with a capital letter to distinguish them from regular functions. This naming convention helps developers quickly identify which functions are meant to be used with `new`.

## Examples

Example of **incorrect** code:
```javascript
function person(name) {
  this.name = name;
}

const user = new person('John');

const colleague = Person();  // calling constructor without new
```

Example of **correct** code:
```javascript
function Person(name) {
  this.name = name;
}

const user = new Person('John');
```