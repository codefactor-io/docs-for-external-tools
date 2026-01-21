Pattern: Missing use of condition list

Issue: -

## Description

Using a condition list improves readability and makes it easier to add or remove conditions in the future. It also allows for better formatting and alignment of conditions. All in all, it’s the idiomatic way to write conditions in Swift.

Since function calls with trailing closures trigger a warning in the Swift compiler when used in conditions, this rule makes sure to wrap such expressions in parentheses when transforming them to condition list elements. The scope of the parentheses is limited to the function call itself.

Examples of **correct** code:

```swift
if a, b {}
```

Examples of **incorrect** code:

```swift
if a ↓&& b {}
```

## Further Reading

* [SwiftLint - Prefer Condition List](https://realm.github.io/SwiftLint/prefer_condition_list.html)