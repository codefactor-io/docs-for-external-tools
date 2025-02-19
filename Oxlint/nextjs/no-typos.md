Pattern: Data fetching function typo

Issue: -

## Description

Common typos in Next.js data fetching function names prevent them from working correctly. These functions must be named exactly as specified in the Next.js documentation.

## Examples

Example of **incorrect** code:
```javascript
export async function getServurSideProps() {
  return { props: {} }
}

export async function getstaticprops() {
  return { props: {} }
}
```

Example of **correct** code:
```javascript
export async function getServerSideProps() {
  return { props: {} }
}

export async function getStaticProps() {
  return { props: {} }
}
```