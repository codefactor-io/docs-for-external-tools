Pattern: Use of global function

Issue: -

## Description

Globally scoped functions override existing functions within the sessions with matching names. This name collision can cause difficult to debug issues for consumers of modules.  

To understand more about scoping, see `Get-Help about_Scopes`.

## How

Use other scope modifiers for functions.

Example of **incorrect** code:

``` PowerShell
function global:functionName {}
```

Example of **correct** code:

``` PowerShell
function functionName {} 
```

## Further Reading

* [PSScriptAnalyzer - AvoidGlobalFunctions](https://github.com/PowerShell/PSScriptAnalyzer/tree/master/docs/Rules/AvoidGlobalFunctions.md)
