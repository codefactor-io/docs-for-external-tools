Pattern: Use of `async` without `await`

Issue: -

## Description

Declaration should not be async if it doesn’t use await.

Examples of **correct** code:

```swift
func test() {
    func test() async {
        await test()
    }
}
```

Examples of **incorrect** code:

```swift
func test() ↓async {
    perform()
}
```

## Further Reading

* [SwiftLint - Async Without Await](https://realm.github.io/SwiftLint/async_without_await.html)