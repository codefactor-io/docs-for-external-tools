Pattern: Missing alternative text

Issue: -

## Description

Images and other elements requiring alternative text must have meaningful descriptions for screen reader users. The alt text should describe the purpose or content of the element.

## Examples

Example of **incorrect** code:
```jsx
<img src="logo.png" />
<img src="banner.jpg" alt="" />
<input type="image" src="submit.png" />
```

Example of **correct** code:
```jsx
<img src="logo.png" alt="Company Logo" />
<img src="banner.jpg" alt="Summer Sale - 50% off all items" />
<input type="image" src="submit.png" alt="Submit Form" />
```