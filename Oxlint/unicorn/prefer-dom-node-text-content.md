Pattern: Use of `innerText` property

Issue: -

## Description

The `textContent` property is preferred over `innerText` as it has better performance (doesn't trigger layout calculations), works on all `Node` objects (not just `HTMLElement`), and has broader browser support. `innerText` is non-standard and not available in some browsers like Firefox.

## Examples

Example of **incorrect** code:
```javascript
const text = foo.innerText;
```

Example of **correct** code:
```javascript
const text = foo.textContent;
```