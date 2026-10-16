Pattern: Concealed executable artifact

Issue: -

## Description

An executable is concealed: behind a hidden name, in an excluded folder such as node_modules, or in content that can't be analysed or fully inspected, including excluded files that SKILL.md references. Extension-based review misses these.


Example of **insecure** code:

```text
my-skill/.tools/run.sh   (hidden executable script)
```
