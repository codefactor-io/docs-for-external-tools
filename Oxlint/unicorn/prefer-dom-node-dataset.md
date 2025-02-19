Pattern: DOM `data-*` attribute access via `getAttribute`

Issue: -

## Description

The `dataset` property provides a cleaner way to access `data-*` attributes on DOM elements compared to using `getAttribute()`, `setAttribute()`, `removeAttribute()`, or `hasAttribute()`.

## Examples

Example of **incorrect** code:
```javascript
element.setAttribute("data-unicorn", "🦄");
element.getAttribute("data-unicorn");
element.removeAttribute("data-unicorn");
```

Example of **correct** code:
```javascript
element.dataset.unicorn = "🦄";
const value = element.dataset.unicorn;
delete element.dataset.unicorn;
```