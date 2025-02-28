Pattern: Body parameter with GET/HEAD fetch request

Issue: -

## Description

Providing a body with `GET` or `HEAD` requests in `fetch()` or `new Request()` calls will cause a `TypeError`. These request methods don't support request bodies according to HTTP specifications.

## Examples

Example of **incorrect** code:
```javascript
const response = await fetch("/", { method: "GET", body: "foo=bar" });
const request = new Request("/", { method: "HEAD", body: "foo=bar" });
```

Example of **correct** code:
```javascript
const response = await fetch("/", { method: "POST", body: "foo=bar" });
const request = new Request("/", { method: "POST", body: "foo=bar" });
```