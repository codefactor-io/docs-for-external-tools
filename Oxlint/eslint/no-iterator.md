Pattern: Use of `__iterator__` property

Issue: -

## Description

The `__iterator__` property is an obsolete SpiderMonkey extension that was used to create custom iterators. Modern JavaScript provides the `Symbol.iterator` protocol for creating iterable objects. Using `__iterator__` reduces compatibility and maintainability.

## Examples

Example of **incorrect** code:
```javascript
Foo.prototype.__iterator__ = function() {
  return new FooIterator(this);
};

obj.__iterator__ = function() {
  // custom iterator
};

foo["__iterator__"] = function() {};
```

Example of **correct** code:
```javascript
Foo.prototype[Symbol.iterator] = function() {
  return new FooIterator(this);
};

class MyIterable {
  *[Symbol.iterator]() {
    yield* this.items;
  }
}

const iter = {
  *[Symbol.iterator]() {
    yield 1;
    yield 2;
  }
};
```