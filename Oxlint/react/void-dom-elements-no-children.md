Pattern: Children in void DOM element

Issue: -

## Description

Void DOM elements (like `<img>`, `<br>`, `<hr>`) are self-closing tags that cannot contain children. Attempting to pass children to these elements through JSX children, the `children` prop, or `dangerouslySetInnerHTML` will not work.

## Examples

Example of **incorrect** code:
```jsx
<br>Children</br>
<br children='Children' />
<br dangerouslySetInnerHTML={{ __html: 'HTML' }} />
React.createElement('br', undefined, 'Children')
```

Example of **correct** code:
```jsx
<div>Children</div>
<div children='Children' />
<div dangerouslySetInnerHTML={{ __html: 'HTML' }} />
React.createElement('div', { children: 'Children' })
```