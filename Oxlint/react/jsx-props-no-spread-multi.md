Pattern: Multiple spread of same JSX props expression

Issue: -

## Description

Spreading the same props expression multiple times in a JSX element can cause unintended prop overrides and unnecessary computations. Each unique props expression should only be spread once.

## Examples

Example of **incorrect** code:
```jsx
<App {...props} myAttr="1" {...props} />
```

Example of **correct** code:
```jsx
<App myAttr="1" {...props} />
<App {...props} myAttr="1" />
```