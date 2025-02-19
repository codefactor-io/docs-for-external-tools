Pattern: Use of accessKey attribute

Issue: -

## Description

The accessKey attribute creates keyboard shortcuts that can conflict with default screen reader and keyboard user commands. These conflicts create accessibility issues and should be avoided.

## Examples

Example of **incorrect** code:
```jsx
<button accessKey="s">Save</button>
<div accessKey="h">Help</div>
<a accessKey="m" href="/menu">Menu</a>
```

Example of **correct** code:
```jsx
<button>Save</button>
<div>Help</div>
<a href="/menu">Menu</a>
```