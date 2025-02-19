Pattern: Unnecessary `Fragment` usage

Issue: -

## Description

React `Fragment`s are useful for grouping multiple children without adding extra DOM nodes. However, when a fragment contains only a single child element, string, or expression, it becomes unnecessary and should be removed to reduce code complexity.

## Examples

Example of **incorrect** code:
```jsx
<>foo</>
<div><>foo</></div>
```

Example of **correct** code:
```jsx
<>foo <div></div></>
<div>foo</div>
```