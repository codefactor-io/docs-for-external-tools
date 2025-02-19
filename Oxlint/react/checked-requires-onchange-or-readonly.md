Pattern: Controlled input without handler or `readonly`

Issue: -

## Description

When using the `checked` prop on an input element, you must either provide an `onChange` handler or mark it as `readonly`. Using both `checked` and `defaultChecked` together creates conflicting controlled/uncontrolled behavior.

## Examples

Example of **incorrect** code:
```jsx
<input type="checkbox" checked />
<input type="checkbox" checked defaultChecked />
<input type="radio" checked defaultChecked />

React.createElement('input', { checked: false });
```

Example of **correct** code:
```jsx
<input type="checkbox" checked onChange={() => {}} />
<input type="checkbox" checked readOnly />
<input type="checkbox" defaultChecked />

React.createElement('input', { type: 'checkbox', checked: true, onChange() {} });
```