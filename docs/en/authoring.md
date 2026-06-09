# Authoring a package

[← Documentation index](../../README.md) · [日本語](../ja/authoring.md)

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
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libusb
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
      "version": ">=1.0.0 & <2.0.0",
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
| `examples` | array | optional | PHP usage snippets. Each string is printed when `pnl install` finishes, so users immediately see how to call the package. Keep them short and runnable, and mirror them in the package README. |
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
    "version": ">=1.0.0 & <2.0.0",
    "required": true
  }
}
```

Requirement fields:

| Field | Required | Meaning |
| --- | --- | --- |
| `symbol_prefix` | optional | C function prefix to keep. Only declarations whose names start with it are wrapped (e.g. `libnfc` exports `nfc_*`). Set it to `""` to keep **every** declaration and pass an inline header straight through without libclang filtering. When omitted, it defaults to a prefix derived from the library key. |
| `library_names` | yes | Candidate shared-library filenames to search for in `load_paths`, environment paths, and system defaults. Each entry is either a string, or an object `{ "name": "libc.dylib", "virtual": true }` — see [Virtual libraries](#virtual-libraries). |
| `header_names` | optional | Candidate public C header paths, expanded from the resolved include root. Omit when you supply `header_inline` or `header_url`. |
| `header_inline` | optional | C declarations embedded directly in the manifest, used verbatim instead of reading a header from disk. See [Inline headers](#inline-headers). |
| `library_url` | optional | Remote source (`http(s)`/`ftp`/`git`) to fetch the native library from instead of searching the local library path. |
| `header_url` | optional | Remote source (`http(s)`/`ftp`/`git`) to fetch the C header from. |
| `version` | yes | Native library version constraint (e.g. `>=1.0.0 & <2.0.0`). |
| `required` | yes | Whether this native requirement is mandatory. Current generation expects required native libraries. |

A requirement needs exactly one header source: `header_names`, `header_inline`, or `header_url`.

#### Inline headers

`header_inline` declares the C API right inside `pnlx.json` — ideal for small or system libraries where shipping or locating a real header is unnecessary. The string is treated as a C header.

```json
"requires": {
  "libc": {
    "symbol_prefix": "",
    "library_names": [
      { "name": "libc.dylib", "virtual": true },
      { "name": "libc.so.6", "virtual": true }
    ],
    "header_inline": "int printf(const char *format);\nint puts(const char *s);\n",
    "version": ">=0.0.0",
    "required": true
  }
}
```

- With `symbol_prefix` set to `""`, the inline header is used as-is (no libclang pass), so write exactly the declarations you want exposed.
- Variadic functions (`...`) cannot be wrapped; declare a fixed-arity signature instead (e.g. `int printf(const char *format);`).

#### Virtual libraries

Some libraries are provided by the operating system and have **no file on disk** to resolve — most notably `libc`, which on macOS lives only in the dyld shared cache. Mark such entries `"virtual": true`:

```json
"library_names": [
  { "name": "libc.dylib", "virtual": true },
  { "name": "libc.so.6", "virtual": true },
  { "name": "msvcrt.dll", "virtual": true }
]
```

A virtual library is **linked by name** and never required to exist as a file. pnl still prefers a real on-disk match when a non-virtual entry resolves; the virtual entry is the fallback.

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
