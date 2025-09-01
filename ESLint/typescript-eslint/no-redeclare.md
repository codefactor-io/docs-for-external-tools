Pattern: Variable redeclaration

Issue: -

## Description

In JavaScript, it’s possible to redeclare the same variable name using `var`. This can lead to confusion as to where the variable is actually declared and initialized.

Examples of *incorrect* code for this rule:

```js
var a = 3;
var a = 10;

class C {
    foo() {
        var b = 3;
        var b = 10;
    }

    static {
        var c = 3;
        var c = 10;
    }
}
```

Examples of correct code for this rule:

```js
var a = 3;
a = 10;

class C {
    foo() {
        var b = 3;
        b = 10;
    }

    static {
        var c = 3;
        c = 10;
    }
}
```