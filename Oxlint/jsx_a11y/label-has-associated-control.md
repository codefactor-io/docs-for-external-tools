Pattern: Unassociated form label

Issue: -

## Description

Form labels must be associated with their controls either through nesting or using the htmlFor attribute. Unassociated labels prevent screen reader users from understanding the purpose of form controls.

## Examples

Example of **incorrect** code:
```jsx
<label>Name</label>
<input type="text" />

<label>Email</label>
<CustomInput />
```

Example of **correct** code:
```jsx
<label htmlFor="name">Name</label>
<input id="name" type="text" />

<label>
  Email
  <input type="email" />
</label>
```