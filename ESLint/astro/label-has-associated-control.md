Pattern: Missing associated control for `label`

Issue: -

## Description

Enforce that a label tag has a text label and an associated control.

There are two supported ways to associate a label with a control:

    Wrapping a control in a label tag.
    Adding `htmlFor` to a label and assigning it a DOM ID string that indicates an input on the page.

This rule checks that any `label` tag (or an indicated custom component that will output a `label` tag) either (1) wraps an `input` element (or an indicated custom component that will output an `input` tag) or (2) has an `htmlFor` attribute and that the `label` tag has text content.
