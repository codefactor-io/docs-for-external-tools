Pattern: Page-specific custom font

Issue: -

## Description

Custom fonts should not be added to individual pages or separate components in _document.js. This prevents Next.js's automatic font optimization and can cause inconsistent font loading across the application.

## Examples

Example of **incorrect** code:
```jsx
// pages/index.js
export default function Page() {
  return (
    <>
      <Head>
        <link href="https://fonts.googleapis.com/css2?family=Roboto" rel="stylesheet" />
      </Head>
      <div>Content</div>
    </>
  )
}
```

Example of **correct** code:
```jsx
// pages/_app.js
import '@fontsource/roboto'

export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```