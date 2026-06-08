# Packages

This directory contains example `pnlx` extension packages. A package is an installable extension root containing `pnlx.json`. During `pnl install`, package files are copied into `@pnlx/packages/<vendor>/<package>`, while source `src/generated` is ignored and regenerated for the current machine.

## Package Lifecycle

Create a new package:

```sh
mkdir -p packages/example
cd packages/example
pnlx init
```

Edit `pnlx.json`, then generate package artifacts:

```sh
pnlx validate
pnlx gen example
```

Install from a project root:

```sh
pnl install packages/example
pnl install file:///absolute/path/to/example
pnl install https://github.com/m3m0r7/pnl-packages/packages/libusb
```

Rebuild installed bridges:

```sh
pnlx build
```

## Writing `pnlx.json`

`pnlx.json` is the extension-side manifest. It identifies the package, declares the generated PHP class, and describes the native libraries and headers required to generate and load the bridge.

Minimal shape:

```json
{
  "schema_version": "2026-07-01",
  "name": "vendor/package",
  "version": "0.1.0",
  "description": "PHP FFI wrapper for a native library.",
  "authors": [
    {
      "name": "Your Name"
    }
  ],
  "license": "MIT",
  "entrypoint": "src/generated/index.php",
  "class": "Pnlx\\Vendor\\Package",
  "platforms": [
    {
      "os": "darwin",
      "arch": "aarch64"
    }
  ],
  "requires": {
    "native-key": {
      "symbol_prefix": "native",
      "library_names": [
        "libnative.dylib",
        "libnative.so",
        "native.dll"
      ],
      "header_names": [
        "native/native.h"
      ],
      "version": ">=1.0.0 <2.0.0",
      "required": true
    }
  },
  "dependencies": {}
}
```

Fields:

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `schema_version` | string | yes | Manifest schema version. Current value is `2026-07-01`. |
| `name` | string | yes | Package identity in `vendor/package` form. This decides install path under `@pnlx/packages`. |
| `version` | string | yes | Package SemVer. This is the extension wrapper version, not necessarily the native library version. |
| `description` | string | yes | Human-readable package summary. |
| `authors` | array | yes | Maintainers or upstream attribution. `email` is optional. |
| `license` | string | yes | Package license expression. Keep upstream native-library licensing clear. |
| `entrypoint` | string | yes | Generated PHP entrypoint, usually `src/generated/index.php`. |
| `class` | string | yes | Fully qualified generated PHP entity class. Must include a namespace. |
| `class_prefix` | string | optional | Prefix applied to generated class/context names. Leave empty unless avoiding class collisions. |
| `platforms` | array | yes | Supported OS/arch combinations for the wrapper package. |
| `requires` | object | yes | Native library requirements. Must contain at least one entry. |
| `dependencies` | object | yes | Other pnl extension dependencies. Dependency solving is not complete yet. |

### Package Identity

`name` controls the installed package path:

```json
"name": "libusb/libusb"
```

installs to:

```text
@pnlx/packages/libusb/libusb
```

The generated PHP namespace is separate. It comes from `class`:

```json
"class": "Pnlx\\Libusb\\Libusb"
```

This generates:

```text
src/generated/Libusb.php
src/generated/LibusbContext.php
```

### Native Requirements

`requires` is keyed by native library identity. The key is used in lock/pathmap files and bridge paths.

Example from libusb:

```json
"requires": {
  "libusb-1.0": {
    "symbol_prefix": "libusb",
    "library_names": [
      "libusb-1.0.dylib",
      "libusb-1.0.so",
      "libusb-1.0.dll"
    ],
    "header_names": [
      "libusb-1.0/libusb.h"
    ],
    "version": ">=1.0.0 <2.0.0",
    "required": true
  }
}
```

Requirement fields:

| Field | Required | Meaning |
| --- | --- | --- |
| `symbol_prefix` | optional | C function prefix to expose. Use it when the library key differs from exported symbol names, e.g. `libnfc` exports `nfc_*`. |
| `library_names` | yes | Candidate shared library filenames to search in `load_paths`, environment paths, and system defaults. |
| `header_names` | yes | Candidate public C header paths. Multiple headers are supported and expanded from the resolved include root. |
| `version` | yes | Native library version constraint. |
| `required` | yes | Whether this native requirement is mandatory. Current generation expects required native libraries. |

### Header And Bridge Generation

`pnlx gen <target>` reads `pnlx.json`, resolves headers, and writes generated artifacts to `src/generated`.

Generated files:

```text
src/generated/<target>.ffi.php
src/generated/<Class>.php
src/generated/<Class>Context.php
src/generated/function.aliases.php
src/generated/<target>.bridge.rs
src/generated/index.php
```

The generated PHP entity exposes concrete methods for discovered native functions and delegates FFI calls through the compiled Rust bridge. The generated Rust bridge exports `pnlx_bridge_*` functions and direct-links the native library.

### Preload And Postload Hooks

If a package has these files beside the generated entrypoint, generated `index.php` requires them:

```text
src/generated/preload.php
src/generated/postload.php
```

`preload.php` runs before optional global function registration. `postload.php` runs after it. Both can access `$runtime` and `$runtimeVarName`.

## Included Packages

- `libusb/libusb`: wrapper package for libusb 1.0, licensed upstream under LGPL-2.1-or-later.
- `libnfc/libnfc`: wrapper package for libnfc, licensed upstream under LGPL-3.0-or-later.
- `libsdl/libsdl`: wrapper package for SDL2, licensed upstream under the Zlib license.
