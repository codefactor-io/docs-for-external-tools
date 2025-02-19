Pattern: Missing HTML language

Issue: -

## Description

The HTML element must specify a valid lang attribute. Without a language specification, screen readers may use incorrect pronunciation rules for the page content.

## Examples

Example of **incorrect** code:
```jsx
<html>
  <body>Hello World</body>
</html>

<html lang="">
  <body>Hello World</body>
</html>
```

Example of **correct** code:
```jsx
<html lang="en">
  <body>Hello World</body>
</html>

<html lang="es">
  <body>Hola Mundo</body>
</html>
```