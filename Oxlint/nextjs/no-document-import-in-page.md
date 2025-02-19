Pattern: Document import outside _document

Issue: -

## Description

The next/document module should only be imported in pages/_document.js. Importing it in other pages can cause unexpected behavior and break Next.js's document lifecycle management.

## Examples

Example of **incorrect** code:
```jsx
// pages/index.js
import Document from 'next/document'

export default function Home() {
  return <div>Home</div>
}
```

Example of **correct** code:
```jsx
// pages/_document.js
import Document from 'next/document'

export default class MyDocument extends Document {
  render() {
    return <Html>...</Html>
  }
}
```