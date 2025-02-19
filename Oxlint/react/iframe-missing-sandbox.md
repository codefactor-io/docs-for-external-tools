Pattern: Missing or invalid `sandbox` attribute on `iframe`

Issue: -

## Description

The `sandbox` attribute provides important security restrictions for `iframe` content. Without proper sandboxing, embedded content may pose security risks. Using `allow-scripts` together with `allow-same-origin` is particularly dangerous as it allows the embedded document to bypass sandbox restrictions entirely.

## Examples

Example of **incorrect** code:
```jsx
<iframe />;
<iframe sandbox="invalid-value" />;
<iframe sandbox="allow-same-origin allow-scripts" />;
```

Example of **correct** code:
```jsx
<iframe sandbox="" />;
<iframe sandbox="allow-origin" />;
```