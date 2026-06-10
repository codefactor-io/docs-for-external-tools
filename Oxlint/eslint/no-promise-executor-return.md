Pattern: Returning value from Promise executor function

Issue: -

## Description

The `new Promise` constructor accepts an executor function as an argument, which has `resolve` and `reject` parameters that can be used to control the state of the created Promise.

The return value of the executor is ignored. Returning a value from an executor function is a possible error because the returned value cannot be used and it doesn't affect the promise in any way.

## Examples

Example of **incorrect** code:

```javascript
new Promise((resolve, reject) => {
  if (someCondition) {
    return defaultResult;
  }
  getSomething((err, result) => {
    if (err) {
      reject(err);
    } else {
      resolve(result);
    }
  });
});

new Promise((resolve, reject) =>
  getSomething((err, data) => {
    if (err) {
      reject(err);
    } else {
      resolve(data);
    }
  }),
);

new Promise(() => {
  return 1;
});
```

Example of **correct** code:

```javascript
new Promise((resolve, reject) => {
  if (someCondition) {
    resolve(defaultResult);
    return;
  }
  getSomething((err, result) => {
    if (err) {
      reject(err);
    } else {
      resolve(result);
    }
  });
});

new Promise((resolve, reject) => {
  getSomething((err, data) => {
    if (err) {
      reject(err);
    } else {
      resolve(data);
    }
  });
});

new Promise((r) => {
  r(1);
});
```