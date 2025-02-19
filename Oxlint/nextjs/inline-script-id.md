Pattern: Missing script id

Issue: -

## Description

Next.js requires inline scripts to have an id attribute for proper hydration. Without an id, inline scripts may not execute correctly during server-side rendering and client-side hydration.

## Examples

Example of **incorrect** code:
```jsx
<script dangerouslySetInnerHTML={{ __html: `console.log('hello')` }} />
```

Example of **correct** code:
```jsx
<script 
  id="my-script"
  dangerouslySetInnerHTML={{ __html: `console.log('hello')` }}
/>
```