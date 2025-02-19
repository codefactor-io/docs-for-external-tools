Pattern: Missing iframe title

Issue: -

## Description

Iframe elements must have a title attribute that describes their content. Without a title, screen reader users cannot efficiently determine the purpose of an iframe without exploring its content.

## Examples

Example of **incorrect** code:
```jsx
<iframe src="map.html" />
<iframe src="video.html" title="" />
<iframe src="form.html" title={undefined} />
```

Example of **correct** code:
```jsx
<iframe
  src="map.html"
  title="Store location map"
/>
<iframe
  src="video.html"
  title="Product demonstration video"
/>
```