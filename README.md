# Build & Install ca65 Action

This action will build and install the cc65 assembler components (ca65, ld65).

* The tip-of-tree version from https://github.com/cc65/cc65 is used.
* Targets are built and installed, so later steps can use the `ca65` and `ld65` commands directly.

The action has no inputs or outputs.

## Example

```yml
name: build

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: a2stuff/build-install-ca65-action@v1
      - name: build
        run: |
          ca65 -o example.o example.s
          ld65 --config example.cfg -o example example.o
```
