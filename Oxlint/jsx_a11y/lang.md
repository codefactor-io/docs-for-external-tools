Pattern: Invalid language code

Issue: -

## Description

The lang attribute on HTML elements must use valid IETF BCP 47 language tags. Invalid language codes prevent screen readers from using the correct pronunciation rules.

## Examples

Example of **incorrect** code:
```jsx
<html lang="english">
  <body>Hello</body>
</html>

<html lang="123">
  <body>Content</body>
</html>
```

Example of **correct** code:
```jsx
<html lang="en">
  <body>Hello</body>
</html>

<html lang="en-US">
  <body>Content</body>
</html>
```