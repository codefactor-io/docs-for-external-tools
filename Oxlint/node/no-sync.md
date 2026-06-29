Pattern: Use of synchronous Node.js method

Issue: -

## Description

In Node.js, most I/O is done through asynchronous methods. However, there are often
synchronous versions of the asynchronous methods. For example, `fs.exists()` and
`fs.existsSync()`. In some contexts, using synchronous operations is okay (if, as with
ESLint, you are writing a command line utility). However, in other contexts the use of
synchronous operations is considered a bad practice that should be avoided.

## Examples

Example of **incorrect** code:
```javascript
fs.existsSync(somePath);

function foo() {
  var contents = fs.readFileSync(somePath).toString();
}
```

Example of **correct** code:
```javascript
obj.sync();

async(function () {
  // ...
});
```
