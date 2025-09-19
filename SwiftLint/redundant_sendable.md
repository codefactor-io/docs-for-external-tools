Pattern: Redundant `Sendable`

Issue: -

## Description

Sendable conformance is redundant on an actor-isolated type.

Examples of **correct** code:

```swift
struct S: Sendable {}
```

Examples of **incorrect** code:

```swift
@MainActor struct ↓S: Sendable {}
```

## Further Reading

* [SwiftLint - Redundant Sendable](https://realm.github.io/SwiftLint/redundant_sendable.html)