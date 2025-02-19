Pattern: next/head import in _document

Issue: -

## Description

The Head component from next/head should not be imported in pages/_document.js. Use the Head component exported from next/document instead for document-level head modifications.

## Examples

Example of **incorrect** code:
```jsx
// pages/_document.js
import Document from 'next/document'
import Head from 'next/head'

export default class MyDocument extends Document {
  render() {
    return (
      <Html>
        <Head />
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    )
  }
}
```

Example of **correct** code:
```jsx
// pages/_document.js
import Document, { Head } from 'next/document'

export default class MyDocument extends Document {
  render() {
    return (
      <Html>
        <Head />
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    )
  }
}
```