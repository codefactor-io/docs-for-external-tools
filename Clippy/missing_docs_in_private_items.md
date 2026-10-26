Pattern: Missing docs on private item

Issue: -

## Description

Doc is good. *rustc* has a `MISSING_DOCS`
allowed-by-default lint for
public members, but has no way to enforce documentation of private items.
This lint fixes that.

## What it does

Warns if there is missing documentation for any private documentable item.

## Further Reading

* [Clippy - missing_docs_in_private_items](https://clippy.rust-lang.org/stable/index.html#missing_docs_in_private_items)
