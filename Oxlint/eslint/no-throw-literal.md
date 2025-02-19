Pattern: Throwing non-Error objects

Issue: -

## Description

Throwing literals or non-Error objects loses the stack trace and other debugging information that Error objects automatically capture. Always throw Error objects or instances of Error subclasses to maintain proper error tracking.

## Examples

Example of **incorrect** code:
```javascript
throw "error";
throw 500;
throw false;
throw null;
throw undefined;
throw { message: "error" };

const err = new Error();
throw "Error: " + err;
throw `${err}`;
```

Example of **correct** code:
```javascript
throw new Error("error");
throw new TypeError("type error");

const err = new Error("error");
throw err;

class CustomError extends Error {
  constructor(message) {
    super(message);
  }
}
throw new CustomError("custom error");
```