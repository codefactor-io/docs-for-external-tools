Pattern: Use of `FileReader` instead of `Blob` methods

Issue: -

## Description

The `FileReader` API predates promises, making it more verbose to use. Modern `Blob` methods like `text()` and `arrayBuffer()` provide cleaner, promise-based alternatives for reading file content.

## Examples

Example of **incorrect** code:
```javascript
async function getData() {
  const arrayBuffer = await new Promise((resolve, reject) => {
    const fileReader = new FileReader();
    fileReader.addEventListener("load", () => {
      resolve(fileReader.result);
    });
    fileReader.addEventListener("error", () => {
      reject(fileReader.error);
    });
    fileReader.readAsArrayBuffer(blob);
  });
}
```

Example of **correct** code:
```javascript
async function getData() {
  const arrayBuffer = await blob.arrayBuffer();
}
```