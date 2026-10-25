# Rainy fork of Lime 8.3.2

Upstream: [openfl/lime](https://github.com/openfl/lime) 8.3.2, MIT.

## No source changes

This repository exists purely for pinning. A Rainy engine checkout needs the
exact Lime it was built against, and `haxelib install lime` resolves to whatever
is current at install time. `haxelib git` on this fork gives the same tree every
time.

The `ndll/Windows64/` payload is the upstream prebuilt set, so cloning this is
enough to build on Windows — no `lime rebuild` needed unless you touch the C++
side.

## Install

```bash
haxelib git lime https://github.com/GengYan0/lime-rainy-fork
```

Pairs with the two forks that do carry changes:

```bash
haxelib git flixel https://github.com/GengYan0/flixel-rainy-fork
haxelib git openfl https://github.com/GengYan0/openfl-rainy-fork
```
