Pattern: Scope on non-th element

Issue: -

## Description

The scope attribute should only be used on th elements in tables. Using scope on other elements can make table navigation harder for screen reader users by providing misleading header information.

## Examples

Example of **incorrect** code:
```jsx
<td scope="col">Header</td>
<div scope="row">Label</div>
<span scope="colgroup">Group</span>
```

Example of **correct** code:
```jsx
<th scope="col">Header</th>
<th scope="row">Label</th>
<th scope="colgroup">Group</th>
```