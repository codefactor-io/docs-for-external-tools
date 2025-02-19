Pattern: DOM node removal via `removeChild`

Issue: -

## Description

The `Node#remove()` method provides a more direct way to remove DOM elements compared to the indirect approach of using `parentNode.removeChild()`.

## Examples

Example of **incorrect** code:
```javascript
parentNode.removeChild(childNode);
```

Example of **correct** code:
```javascript
childNode.remove();
```