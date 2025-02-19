Pattern: Control character in regular expression

Issue: -

## Description

Control characters (ASCII characters 0-31) are rarely used in JavaScript strings. Regular expressions containing patterns that explicitly match these characters are likely mistakes, as they're special, invisible characters that can cause unexpected behavior.

## Examples

Example of **incorrect** code:
```javascript
var pattern1 = /\x00/;
var pattern2 = /\x0C/;
var pattern3 = /\x1F/;
var pattern4 = /\u000C/;
var pattern5 = /\u{C}/u;
var pattern6 = new RegExp("\x0C");
```

Example of **correct** code:
```javascript
var pattern1 = /\x20/;
var pattern2 = /\u0020/;
var pattern3 = /\t/;
var pattern4 = /\n/;
var pattern5 = new RegExp("\x20");
var pattern6 = new RegExp("\\n");
```