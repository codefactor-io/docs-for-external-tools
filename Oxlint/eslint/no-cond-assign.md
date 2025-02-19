Pattern: Assignment operator in conditional expression

Issue: -

## Description

Using assignment operators (=) in conditional expressions is often a typo for comparison operators (==, ===). While there are valid use cases for assignment in conditions, it frequently indicates a mistake that can lead to unexpected behavior.

## Examples

Example of **incorrect** code:
```javascript
if ((user.jobTitle = "manager")) {
  // user.jobTitle is now "manager" instead of comparing
}

while (nextItem = getNextItem()) {
  // ...
}
```

Example of **correct** code:
```javascript
if (user.jobTitle === "manager") {
  // comparison, not assignment
}

let nextItem;
while ((nextItem = getNextItem()) !== null) {
  // explicit parentheses show assignment is intentional
}
```