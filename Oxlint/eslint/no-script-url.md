Pattern: Use of `javascript:` URL

Issue: -

## Description

Using `javascript:` URLs is similar to using eval() as the browser must parse and execute the code in the URL. This can lead to security vulnerabilities and performance issues. Use proper event handlers or other alternatives instead.

## Examples

Example of **incorrect** code:
```javascript
location.href = "javascript:void(0)";
location.assign("javascript:alert('Hello')");

const link = `javascript:doSomething()`;
window.open("javascript:print()");

<a href="javascript:void(0)">Click me</a>
```

Example of **correct** code:
```javascript
location.href = "#";
location.assign("/page");

const link = "#";
window.open("/print");

<a href="#" onClick={doSomething}>Click me</a>
<button onClick={handleClick}>Click me</button>
```