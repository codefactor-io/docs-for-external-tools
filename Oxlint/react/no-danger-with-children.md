Pattern: Conflicting `dangerouslySetInnerHTML` and children

Issue: -

## Description

Using both `children` and `dangerouslySetInnerHTML` on the same element creates a conflict in content rendering. React will throw a warning as these two methods of setting content cannot be used together.

## Examples

Example of **incorrect** code:
```jsx
<div dangerouslySetInnerHTML={{ __html: "HTML" }}>Children</div>;
React.createElement("div", { dangerouslySetInnerHTML: { __html: "HTML" } }, "Children");
```

Example of **correct** code:
```jsx
<div>Children</div>
<div dangerouslySetInnerHTML={{ __html: "HTML" }} />
```