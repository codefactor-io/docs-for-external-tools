Pattern: Duplicate polyfill

Issue: -

## Description

Including polyfills from Polyfill.io that are already included with Next.js increases page size unnecessarily. Next.js includes common polyfills by default.

## Examples

Example of **incorrect** code:
```jsx
<Head>
  <script src="https://polyfill.io/v3/polyfill.min.js?features=Promise,es2015,es6" />
</Head>
```

Example of **correct** code:
```jsx
<Head>
  <script src="https://polyfill.io/v3/polyfill.min.js?features=CustomEvent" />
</Head>
```