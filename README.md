# pnl Packages

This repository contains example `pnlx` extension packages for [pnl](https://github.com/m3m0r7/pnl), a prototype package manager and runtime toolchain for PHP native-library extensions.

A package is an installable extension root containing `pnlx.json`. During `pnl install`, package files are copied into `@pnlx/packages/<vendor>/<package>`, while source `src/generated` is ignored and regenerated for the current machine.

## About pnl

pnl provides two command-line tools:

- **`pnl`** — manages project-side installation, lockfiles, validation, and package listings.
- **`pnlx`** — supports extension authoring, wrapper generation, and Rust bridge rebuilding.

Generated installation files live under `@pnlx/` rather than Composer's `vendor/` directory. Applications load Composer first for SDK dependencies, then `@pnlx/autoload.php` for native extensions.

A project is described by:

- `pnl.json` — editable project manifest.
- `@pnlx/pnlx-lock.json` — platform-specific lockfile.
- `@pnlx/pnlx-pathmap.json` — native library and header path mappings.
- `@pnlx/autoload.php` — PHP entrypoint.

### Requirements

- Rust 1.85+
- PHP 8.2+ with the FFI extension enabled
- Composer 2.x
- Git 2.x
- POSIX `make`

Validated on macOS/aarch64 with Homebrew package management.

### Installation Sources

`pnl install` accepts several source forms:

- Local filesystem paths
- `file://` URLs
- GitHub HTTPS URLs
- Git SSH URLs with an optional branch
- Git repositories whose root contains `pnlx.json`

```sh
pnl install packages/libusb
pnl install file:///absolute/path/to/libusb
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libusb
```

### PHP Usage

Applications interact with native libraries through generated entity classes. A typical workflow loads the `Runtime`, retrieves a native library entity, and calls generated wrapper methods:

```php
$runtime = new Runtime(__DIR__);
$libusb = $runtime->load(Libusb::class);
$result = $libusb->libusbInit(null);
```

Generated code supports both entity methods and optional global PHP functions, controlled by the `enables.use_functions` configuration setting.

> **Status:** pnl is an early implementation. Local path, `file://`, and git-based installations work today. Repository index solving, signed package indexes, and archive downloaders are still in design.

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

Each package wraps a native library. The `License` column reflects the upstream native library's licensing — the wrapper manifests only describe how to locate and bind to that library.

| Package | Base library | License |
| --- | --- | --- |
| `libusb/libusb` | libusb 1.0 | LGPL-2.1-or-later |
| `libnfc/libnfc` | libnfc | LGPL-3.0-or-later |
| `libsdl/libsdl` | SDL2 | Zlib |
| `libcurl/libcurl` | libcurl | MIT |
| `zlib/zlib` | zlib | Zlib |
| `libsqlite3/libsqlite3` | SQLite3 | blessing |
| `libpng/libpng` | libpng | libpng-2.0 |
| `libjpeg/libjpeg` | libjpeg-turbo | IJG |
| `openssl/openssl` | OpenSSL | Apache-2.0 |
| `libxml2/libxml2` | libxml2 | MIT |
| `libzip/libzip` | libzip | BSD-3-Clause |
| `libgit2/libgit2` | libgit2 | GPL-2.0-with-GCC-exception |
| `libssh2/libssh2` | libssh2 | BSD-3-Clause |
| `libsodium/libsodium` | libsodium | ISC |
| `libpcre2/libpcre2` | PCRE2 | BSD-3-Clause |
| `libuv/libuv` | libuv | MIT |
| `libzstd/libzstd` | Zstandard | BSD-3-Clause |
| `liblz4/liblz4` | LZ4 | BSD-2-Clause |
| `libwebp/libwebp` | libwebp | BSD-3-Clause |
| `libfreetype/libfreetype` | FreeType | FTL |
| `libpq/libpq` | libpq (PostgreSQL) | PostgreSQL |
| `libhiredis/libhiredis` | hiredis | BSD-3-Clause |
| `libyaml/libyaml` | libyaml | MIT |
| `libcjson/libcjson` | cJSON | MIT |
| `libmagic/libmagic` | libmagic | BSD-2-Clause |
| `libgmp/libgmp` | GMP | LGPL-3.0-or-later |
| `libncurses/libncurses` | ncurses | X11 |
| `libreadline/libreadline` | GNU Readline | GPL-3.0-or-later |
| `libzmq/libzmq` | ZeroMQ | MPL-2.0 |
| `libmosquitto/libmosquitto` | Mosquitto (MQTT) | EPL-2.0 |
| `libtiff/libtiff` | libtiff | libtiff |
| `libcairo/libcairo` | cairo | LGPL-2.1-or-later |
| `libglfw/libglfw` | GLFW | Zlib |
| `libopus/libopus` | Opus | BSD-3-Clause |
| `libsndfile/libsndfile` | libsndfile | LGPL-2.1-or-later |
| `libduckdb/libduckdb` | DuckDB | MIT |
| `libevent/libevent` | libevent | BSD-3-Clause |
| `libxxhash/libxxhash` | xxHash | BSD-2-Clause |
| `libsnappy/libsnappy` | Snappy | BSD-3-Clause |
| `libbz2/libbz2` | bzip2 | bzip2-1.0.6 |
| `liblzma/liblzma` | xz / liblzma | 0BSD |
| `libbrotli/libbrotli` | Brotli | MIT |
| `libarchive/libarchive` | libarchive | BSD-2-Clause |
| `libargon2/libargon2` | Argon2 | Apache-2.0 |
| `libgcrypt/libgcrypt` | Libgcrypt | LGPL-2.1-or-later |
| `libmbedtls/libmbedtls` | Mbed TLS | Apache-2.0 |
| `libnettle/libnettle` | Nettle | LGPL-3.0-or-later |
| `libssh/libssh` | libssh | LGPL-2.1-only |
| `libmariadb/libmariadb` | MariaDB Connector/C | LGPL-2.1-or-later |
| `liblmdb/liblmdb` | LMDB | OLDAP-2.8 |
| `libleveldb/libleveldb` | LevelDB | BSD-3-Clause |
| `librocksdb/librocksdb` | RocksDB | Apache-2.0 |
| `libnghttp2/libnghttp2` | nghttp2 | MIT |
| `libwebsockets/libwebsockets` | libwebsockets | MIT |
| `libmicrohttpd/libmicrohttpd` | GNU libmicrohttpd | LGPL-2.1-or-later |
| `libcares/libcares` | c-ares | MIT |
| `libpcap/libpcap` | libpcap | BSD-3-Clause |
| `libjansson/libjansson` | Jansson | MIT |
| `libmsgpack/libmsgpack` | msgpack-c | BSL-1.0 |
| `libprotobufc/libprotobufc` | protobuf-c | BSD-2-Clause |
| `libexpat/libexpat` | Expat | MIT |
| `libicu/libicu` | ICU | ICU |
| `libidn2/libidn2` | libidn2 | LGPL-3.0-or-later |
| `liboniguruma/liboniguruma` | Oniguruma | BSD-2-Clause |
| `libutf8proc/libutf8proc` | utf8proc | MIT |
| `libavcodec/libavcodec` | FFmpeg libavcodec | LGPL-2.1-or-later |
| `libavformat/libavformat` | FFmpeg libavformat | LGPL-2.1-or-later |
| `libavutil/libavutil` | FFmpeg libavutil | LGPL-2.1-or-later |
| `libswscale/libswscale` | FFmpeg libswscale | LGPL-2.1-or-later |
| `libgd/libgd` | GD | GD |
| `libgif/libgif` | giflib | MIT |
| `libexif/libexif` | libexif | LGPL-2.1-or-later |
| `libheif/libheif` | libheif | LGPL-3.0-or-later |
| `libavif/libavif` | libavif | BSD-2-Clause |
| `libharfbuzz/libharfbuzz` | HarfBuzz | MIT |
| `libpixman/libpixman` | Pixman | MIT |
| `libportaudio/libportaudio` | PortAudio | MIT |
| `libopenal/libopenal` | OpenAL Soft | LGPL-2.1-or-later |
| `libvorbis/libvorbis` | Vorbis | BSD-3-Clause |
| `libogg/libogg` | Ogg | BSD-3-Clause |
| `libflac/libflac` | FLAC | BSD-3-Clause |
| `libmpg123/libmpg123` | mpg123 | LGPL-2.1-only |
| `libsamplerate/libsamplerate` | libsamplerate | BSD-2-Clause |
| `libglew/libglew` | GLEW | BSD-3-Clause |
| `libvulkan/libvulkan` | Vulkan | Apache-2.0 |
| `libuuid/libuuid` | util-linux libuuid | BSD-3-Clause |
| `libdbus/libdbus` | D-Bus | AFL-2.1 |
| `libffi/libffi` | libffi | MIT |
| `libserialport/libserialport` | libserialport | LGPL-3.0-or-later |
| `libftdi/libftdi` | libftdi1 | LGPL-2.1-only |
| `libhidapi/libhidapi` | HIDAPI | BSD-3-Clause |
| `librtlsdr/librtlsdr` | librtlsdr | GPL-2.0-or-later |
| `libmodbus/libmodbus` | libmodbus | LGPL-2.1-or-later |
| `libfftw3/libfftw3` | FFTW | GPL-2.0-or-later |
| `libgsl/libgsl` | GSL | GPL-3.0-or-later |
| `libmpfr/libmpfr` | MPFR | LGPL-3.0-or-later |
| `libopenblas/libopenblas` | OpenBLAS | BSD-3-Clause |
| `liblua/liblua` | Lua | MIT |
| `libquickjs/libquickjs` | QuickJS | MIT |
| `libduktape/libduktape` | Duktape | MIT |
| `libtreesitter/libtreesitter` | Tree-sitter | MIT |
| `libtcc/libtcc` | TinyCC | LGPL-2.1-or-later |
| `libtidy/libtidy` | HTML Tidy | W3C |
| `libgumbo/libgumbo` | Gumbo | Apache-2.0 |
| `libcmark/libcmark` | cmark | BSD-2-Clause |
