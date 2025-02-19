Pattern: Use of `on-` event handler properties

Issue: -

## Description

Using `on-` event handler properties (`onclick`, `onload`, etc.) limits you to one handler per event. The `addEventListener()` method allows multiple handlers and provides more features like event capture and one-time handling.

## Examples

Example of **incorrect** code:
```javascript
foo.onclick = () => {};
element.onload = () => {};
```

Example of **correct** code:
```javascript
foo.addEventListener("click", () => {});
element.addEventListener("load", () => {});
```