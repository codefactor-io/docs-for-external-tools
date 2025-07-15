Pattern: Use of global alias

Issue: -

## Description

Globally scoped aliases override existing aliases within the sessions with matching names. This name collision can cause difficult to debug issues for consumers of modules and scripts.

To understand more about scoping, see `Get-Help about_Scopes`.

## How

Use other scope modifiers for new aliases.

Example of **incorrect** code:

``` PowerShell
New-Alias -Name Name -Value Value -Scope "Global"
```

Example of **correct** code:

``` PowerShell
New-Alias -Name Name1 -Value Value
```

## Further Reading

* [PSScriptAnalyzer - AvoidGlobalAliases](https://github.com/PowerShell/PSScriptAnalyzer/tree/master/docs/Rules/AvoidGlobalAliases.md)
