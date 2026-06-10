Pattern: Interactive element without label

Issue: -

## Description

An interactive element (such as a `<button>`) without an accessible text label makes it difficult or impossible for users of assistive technologies to understand the purpose of the control.

## Examples

Example of **incorrect** code:

```jsx
<button />
<input type="text" />
<a href="/path" />
<th />
<div role="button" />
<div role="checkbox" />
```

Example of **correct** code:

```jsx
<button>Save</button>
<button aria-label="Save" />
<label>Name <input type="text" /></label>
<a href="/path">Learn more</a>
<th>Column Header</th>
<div role="button">Submit</div>
<div role="checkbox" aria-labelledby="label_id" />
```