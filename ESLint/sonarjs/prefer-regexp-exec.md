Pattern: Missing use of `RegExp.exec()`

Issue: -

## Description

`String.match()` behaves the same way as `RegExp.exec()` when the regular expression does not include the global flag `g`. While they work the same, `RegExp.exec()` can be slightly faster than `String.match()`. Therefore, it should be preferred for better performance.


Example of **incorrect** code:

```ts
'foo'.match(/bar/);
```

Example of **correct** code:

```ts
/bar/.exec('foo');
```

## Further Reading

* [prefer-regexp-exec](https://sonarsource.github.io/rspec/#/rspec/S6594/javascript)