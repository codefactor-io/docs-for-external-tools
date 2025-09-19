Pattern: Implicit optional initialization

Issue: -

## Description

Optionals should be consistently initialized, either with `= nil` or without.

Examples of **correct** code:

```swift
//
// style: never
//

private var myVar: Int? = nil


//
// style: always
//

public var myVar: Int?

```

Examples of **incorrect** code:

```swift
//
// style: never
//

var ↓myVar: Int? 

//
// style: always
//

var ↓myVar: Int? = nil
```

## Further Reading

* [SwiftLint - Implicit Optional Initialization](https://realm.github.io/SwiftLint/implicit_optional_initialization.html)