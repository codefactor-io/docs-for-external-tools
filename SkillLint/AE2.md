Pattern: Misleading File Extension

Issue: -

## Description

A file's extension contradicts its content, for example a `.png` that is really a script or a `.txt` that holds a binary. Misleading extensions hide content from review.


Example of **insecure** code:

```text
image.png   (starts with #!/bin/sh)
```
