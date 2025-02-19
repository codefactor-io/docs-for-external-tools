Pattern: Duplicate prop names in JSX element

Issue: -

## Description

Using duplicate props in JSX elements is likely a mistake and can cause unexpected behavior, as later props will override earlier ones. Each prop name should appear only once in a JSX element.

## Examples

Example of **incorrect** code:
```jsx
<App a a />;
<App foo={2} bar baz foo={3} />;
```

Example of **correct** code:
```jsx
<App a />;
<App bar baz foo={3} />;
```