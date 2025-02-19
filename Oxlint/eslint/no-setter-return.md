Pattern: Return statement in setter

Issue: -

## Description

Setter methods are designed to modify state, not return values. Any value returned from a setter is ignored by JavaScript. Including a return statement in a setter likely indicates a misunderstanding of how setters work.

## Examples

Example of **incorrect** code:
```javascript
class MyClass {
  set value(val) {
    this._value = val;
    return val;
  }
}

const obj = {
  set name(value) {
    this._name = value;
    return true;
  }
};

class Storage {
  set items(values) {
    this.store = values;
    return this.store;
  }
}
```

Example of **correct** code:
```javascript
class MyClass {
  set value(val) {
    this._value = val;
  }
}

const obj = {
  set name(value) {
    this._name = value;
  }
};

class Storage {
  set items(values) {
    this.store = values;
  }
  
  getItems() {
    return this.store;
  }
}
```