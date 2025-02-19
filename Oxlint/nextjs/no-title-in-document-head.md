Pattern: Title in document head

Issue: -

## Description

Title tags should not be added in pages/_document.js as they will be static and cannot be changed dynamically. Use title tags in individual pages or _app.js instead.

## Examples

Example of **incorrect** code:
```jsx
// pages/_document.js
export default function Document() {
  return (
    <Html>
      <Head>
        <title>Static Title</title>
      </Head>
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
// pages/index.js
export default function Page() {
  return (
    <>
      <Head>
        <title>Dynamic Page Title</title>
      </Head>
      <main>Content</main>
    </>
  )
}
```