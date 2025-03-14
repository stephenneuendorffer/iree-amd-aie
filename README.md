# AMD AIE Plugin for IREE

This repository contains an early-phase IREE compiler and runtime plugin for
interfacing the AMD AIE accelerator to IREE.

## Developer Setup

These instructions assume that you have an appropriate IREE checkout side by side
with this repository have an IREE build setup in an `iree-build` directory that
is also a sibling. This is not a requirement, but instructions will need to be
changed for different paths.

Preparing repostiory:

```
git submodule update --init
```

## Enabling in IREE

```
cd ../iree-build
cmake -DIREE_COMPILER_PLUGIN_PATHS=../iree-amd-aie .
ninja
```

Lit tests specific to AIE can be run with something like:

```
ctest -R amd-aie
```
