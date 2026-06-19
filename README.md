# pnl Packages

[日本語版](README.ja.md)

This repository contains the official `pnlx` extension packages for [pnl](https://github.com/m3m0r7/pnl), a package manager and runtime toolchain for PHP native-library extensions.

A package is an installable extension root containing `pnlx.json`. During `pnl install`, package files are copied into `@pnlx/packages/<vendor>/<package>`, while source `src/generated` is ignored and regenerated for the current machine.

`packages/repository-index.json` is a generated catalogue of every package and version. It lets `pnl search` browse this repository over HTTP without cloning. Regenerate it whenever packages or versions change:

```sh
pnl repo index packages \
  --base-url https://github.com/m3m0r7/pnl-packages/tree/main/packages
```

## Documentation

- [About pnl](docs/en/about.md) — How pnl/pnlx work, requirements, and install sources.
- [Authoring a package](docs/en/authoring.md) — The package lifecycle and the full `pnlx.json` reference (incl. inline headers and virtual libraries).
- [Included packages](docs/en/packages.md) — The list of bundled packages and their licenses.
