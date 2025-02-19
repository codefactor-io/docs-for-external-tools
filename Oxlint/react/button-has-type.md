Pattern: Missing or invalid `type` attribute on `button`

Issue: -

## Description

The default `type` for HTML button elements is "submit", which can cause unexpected page reloads. Buttons should explicitly specify their type as either "button", "submit", or "reset" to ensure intended behavior.

## Examples

Example of **incorrect** code:
```jsx
<button />
<button type="foo" />
```

Example of **correct** code:
```jsx
<button type="button" />
<button type="submit" />
```