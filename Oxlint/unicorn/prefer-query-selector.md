Pattern: Legacy DOM selector methods

Issue: -

## Description

The `querySelector()` and `querySelectorAll()` methods provide a more flexible and consistent way to select DOM elements compared to `getElementById()`, `getElementsByClassName()`, and `getElementsByTagName()`. Using a single query method allows for more specific selectors and better maintainability.

## Examples

Example of **incorrect** code:
```javascript
document.getElementById("foo");
document.getElementsByClassName("foo bar");
document.getElementsByTagName("main");
document.getElementsByClassName(fn());
```

Example of **correct** code:
```javascript
document.querySelector("#foo");
document.querySelector(".bar");
document.querySelector("main #foo .bar");
document.querySelectorAll(".foo .bar");
document.querySelectorAll("li a");
document.querySelector("li").querySelectorAll("a");
```