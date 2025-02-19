Pattern: Regular expression starting with `=`

Issue: -

## Description

Using `=` at the beginning of a regular expression can be mistaken for a division assignment operator (e.g., `/=`). This confusion can lead to bugs and reduced code readability.

## Examples

Example of **incorrect** code:
```javascript
function bar() {
  return /=foo/;
}

const regex = /=test/;
```

Example of **correct** code:
```javascript
function bar() {
  return /[=]foo/;
}

const regex = /\=test/;
```