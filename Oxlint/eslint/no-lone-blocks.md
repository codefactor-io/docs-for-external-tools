Pattern: Unnecessary standalone block

Issue: -

## Description

Standalone block statements that don't create new scope (with let/const) or aren't part of control flow statements serve no purpose. They add unnecessary nesting and can mislead readers about scope or intent.

## Examples

Example of **incorrect** code:
```javascript
{
  var x = 1;  // var doesn't create block scope
}

function foo() {
  {
    doSomething();
  }
}

{
  {
    console.log("nested blocks");
  }
}
```

Example of **correct** code:
```javascript
{
  let x = 1;  // creates block scope
  const y = 2;
}

if (condition) {
  doSomething();
}

function foo() {
  doSomething();
}

// For creating block scope
{
  let private = "scoped";
  handlePrivate();
}
```