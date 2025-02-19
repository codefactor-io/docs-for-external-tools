Pattern: Missing Google Fonts preconnect

Issue: -

## Description

When using Google Fonts, you should include a preconnect link to improve loading performance. The preconnect hint allows the browser to set up early connections before an HTTP request is sent.

## Examples

Example of **incorrect** code:
```jsx
<Head>
  <link href="https://fonts.googleapis.com/css2?family=Roboto" rel="stylesheet" />
</Head>
```

Example of **correct** code:
```jsx
<Head>
  <link rel="preconnect" href="https://fonts.gstatic.com" />
  <link href="https://fonts.googleapis.com/css2?family=Roboto" rel="stylesheet" />
</Head>
```