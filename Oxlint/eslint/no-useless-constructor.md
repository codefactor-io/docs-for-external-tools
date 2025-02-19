Pattern: Constructor that only calls super or is empty

Issue: -

## Description

ES2015 classes provide an implicit constructor when none is specified. Empty constructors or constructors that only delegate to the parent class constructor using super() are unnecessary and can be safely removed.

## Examples

Example of **incorrect** code:
```javascript
class Empty {
  constructor() {
  }
}

class Parent extends Base {
  constructor(props) {
    super(props);
  }
}

class Child extends Parent {
  constructor(...args) {
    super(...args);
  }
}
```

Example of **correct** code:
```javascript
class Empty {
  // no constructor needed
}

class Parent extends Base {
  // constructor is implicit
}

class Child extends Parent {
  constructor(props) {
    super(props);
    this.state = {};  // Does something more
  }
}

class Other {
  constructor() {
    doSomething();  // Has other logic
  }
}
```