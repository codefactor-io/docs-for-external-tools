Pattern: Styled JSX in document

Issue: -

## Description

Styled JSX should not be used in pages/_document.js as it won't be processed correctly. Custom CSS in _document.js should be added using regular style tags or external stylesheets.

## Examples

Example of **incorrect** code:
```jsx
// pages/_document.js
export default function Document() {
  return (
    <Html>
      <Head>
        <style jsx>{`
          body { background: red; }
        `}</style>
      </Head>
      <body><Main /></body>
    </Html>
  )
}
```

Example of **correct** code:
```jsx
// pages/_document.js
export default function Document() {
  return (
    <Html>
      <Head>
        <link rel="stylesheet" href="/styles.css" />
      </Head>
      <body><Main /></body>
    </Html>
  )
}
```