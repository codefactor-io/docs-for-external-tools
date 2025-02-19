Pattern: Multiple Head components

Issue: -

## Description

Using multiple Head components in pages/_document.js causes undefined behavior. The Head component should only be used once to manage document head elements.

## Examples

Example of **incorrect** code:
```jsx
// pages/_document.js
export default function MyDocument() {
  return (
    <Html>
      <Head />
      <Head />
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  )
}
```

Example of **correct** code:
```jsx
// pages/_document.js
export default function MyDocument() {
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
```