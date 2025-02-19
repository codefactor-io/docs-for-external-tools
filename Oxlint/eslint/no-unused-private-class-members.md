Pattern: Unused private class member

Issue: -

## Description

Private class members (#) that are never read are likely mistakes from incomplete refactoring. Only writing to a private member without ever reading it indicates dead code that can be safely removed.

## Examples

Example of **incorrect** code:
```javascript
class Example {
  #unused = 5;
  
  #neverRead = 0;
  setIt() {
    this.#neverRead = 42;  // only writes, never reads
  }
  
  #unusedMethod() {}
  
  get #unusedGetter() {}
  set #unusedSetter(value) {}
  
  #onlyUpdatesItself = 0;
  increment() {
    this.#onlyUpdatesItself++;  // never read elsewhere
  }
}
```

Example of **correct** code:
```javascript
class Example {
  #used = 5;
  getValue() {
    return this.#used;  // member is read
  }
  
  #counter = 0;
  increment() {
    this.#counter++;
    return this.#counter;  // read after write
  }
  
  #helper() {
    return 42;
  }
  calculate() {
    return this.#helper();  // method is called
  }
  
  get #value() { return 42; }
  set #value(v) { this.#processValue(v); }
}
```