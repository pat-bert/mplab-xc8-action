# Build with MPLAB X and XC8 GitHub Action

This action will build a MPLAB X / XC8 project.

It runs on Linux Ubuntu 20.04 and uses:

* [MPLAB X](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-x-ide) v6.20
* [XC8](https://www.microchip.com/en-us/development-tools-tools-and-software/mplab-xc-compilers) v2.50

## Inputs

### `project`

**Required** The path of the project to build (relative to the repository). 

For example: `firmware.X`.

### `packs`

**Optional**: DFPs separated by comma needed for the build.

For example: `ATtiny_DFP=3.1.260`.

### `configuration`

The configuration of the project to build. Defaults to `default`.

## Example Usage

Add the following `.github/workflows/build.yml` file to your project:

```yaml
name: Build
on:
  push:
    branches:
      - master
  pull_request:
    branches:
      - master

jobs:
  build:
    name: Build the project
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Build project with MPLAB X IDE
        uses: aeraterta/mplab-xc8-action@v1.0.0
        with:
          project: firmware.X
          packs: "ATtiny_DFP=3.1.260"
          configuration: default
          mplabx-version: 6.20
          xc8-version: 2.50

```

# Acknowledgements

Inspired by <https://github.com/velocitek/ghactions-mplabx>.  
Forked from <https://github.com/jeandeaual/mplabx-xc8-build-action>.