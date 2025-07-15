Pattern: Disallow !important

Issue: Use of !important

## Description

The `!important` annotation is used to artificially increase the specificity of a given property value in a rule. This is usually an indication that the specificity of the entire CSS has gotten a bit out of control and needs to be refactored. The more frequently `!important` is found in CSS, the more likely it is that developers are having trouble styling parts of a page effectively.

## Rule Details

Rule ID: `important`

This rule is aimed at keeping your specificity levels in check. As such, it warns whenever `!important` is used.

The following patterns are considered warnings:

```css
.mybox {
    color: red !important;
}

```

## Further Reading

* [Don't use !important](http://james.padolsey.com/usability/dont-use-important/)
* [!important CSS Declarations: How and When to Use Them](http://coding.smashingmagazine.com/2010/11/02/the-important-css-declaration-how-and-when-to-use-it/)
* [When using !important is the right choice](http://css-tricks.com/9462-when-using-important-is-the-right-choice/)
