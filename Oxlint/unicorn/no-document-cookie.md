Pattern: Direct use of `document.cookie`

Issue: -

## Description

Using `document.cookie` directly is error-prone due to its string-based interface. Use the Cookie Store API or a cookie library instead for safer and more maintainable cookie management.

## Examples

Example of **incorrect** code:
```javascript
document.cookie = "foo=bar" + "; Path=/" + "; Domain=example.com" + "; expires=Fri, 31 Dec 9999 23:59:59 GMT" + "; Secure";
```

Example of **correct** code:
```javascript
await cookieStore.set({
  name: "foo",
  value: "bar",
  expires: Date.now() + 24 * 60 * 60 * 1000,
  domain: "example.com"
});
```