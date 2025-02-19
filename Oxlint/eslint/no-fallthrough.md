Pattern: Case statement without break or comment

Issue: -

## Description

Switch statements in JavaScript allow case statements to fall through to the next case when there is no `break`, `return`, or `throw`. While this can be intentional, unmarked fallthroughs are often mistakes. Intentional fallthroughs should be marked with a comment containing "falls through" or similar.

## Examples

Example of **incorrect** code:
```javascript
switch (foo) {
  case 1:
    doSomething();
  case 2:
    doSomethingElse();
  default:
    cleanup();
}
```

Example of **correct** code:
```javascript
switch (foo) {
  case 1:
    doSomething();
    break;
  
  case 2:
    doSomethingElse();
    // falls through
    
  default:
    cleanup();
}

switch (foo) {
  case 1:
  case 2:  // multiple cases sharing code is fine
    sharedOperation();
    break;
    
  case 3:
    return specialOperation();  // return also prevents fallthrough
}
```