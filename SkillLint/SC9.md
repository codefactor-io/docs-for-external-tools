Pattern: Concealed Executable Artifact

Issue: -

## Description

An executable is concealed inside another file: inside an Office document or archive, behind a hidden or misleading name, or in a referenced archive member that couldn't be inspected. Extension-based review misses these.


Example of **insecure** code:

```text
my-skill/assets/report.docx   (contains an embedded .exe)
```
