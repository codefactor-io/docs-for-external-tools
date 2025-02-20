Pattern: RegExp for string boundary check

Issue: -

## Description

Using `String#startsWith()` and `String#endsWith()` is more readable and efficient than regular expressions with `^` or `$` anchors when checking string boundaries. These methods don't require regex parsing overhead.

## Examples

Example of **incorrect** code:
```javascript
const foo = "hello";
/^abc/.test(foo);
```

Example of **correct** code:
```javascript
const foo = "hello";
foo.startsWith("abc");
```