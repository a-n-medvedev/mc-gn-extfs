# mc-gn-extfs
Midnight Commander External VFS (extfs) for browsing GN-generated project.json files

## Overview

A `gnproj` python script allows browsing and building targets specified in GN project
file (`project.json` unless other name is specified in `gn` command line).

Targets are represented as executable files in virtual filesystem. View (`F3`) and Edit (`F4`)
operations on target show textual representation of target properties with actual values.
Run (`Enter`) operation executes `/usr/bin/ninja` tool passing path to working directory and
target name.

To simplify browsing of dependencies, there is additional 'directory' `[ -=DEPS=- ]` in which
targets are represented as directories. Target dependencies and configurations are represented
as directories, other properties are represented as files:
- `deps` directory contains "symlinks" to the corresponding targets allowing the corresponding
  targes to be opened by clicking on it.
- `configs` directory represents list of configs as a list of files; each file name is equal to
  target name (like `//path/to/some:config`)


## Installation

Copy `gnproj` script to `$HOME/.local/share/mc/extfs.d/` directory.

Edit extension file `$HOME/.config/mc/mc.ext` associating `project.json` file with `gnproj`
VFS extension:

```
# GN JSON project file
shell/project.json
    Open=%cd %p/gnproj://
```
