# About pnl

[← Documentation index](../../README.md) · [日本語](../ja/about.md)

## About pnl

pnl provides two command-line tools:

- **`pnl`** — manages project-side installation, lockfiles, validation, and package listings.
- **`pnlx`** — supports extension authoring, wrapper generation, and Rust bridge rebuilding.

Generated installation files live under `@pnlx/` rather than Composer's `vendor/` directory. Applications load Composer first for SDK dependencies, then `@pnlx/autoload.php` for native extensions.

A project is described by:

- `pnl.json` — editable project manifest.
- `pnlx-lock.json` — platform-specific lockfile.
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

Applications interact with native libraries through generated entity classes. A C library is a bag of functions, so the entity is **static** — never instantiated. The first static call boots it automatically:

```php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libusb\Libusb;

$result = Libusb::libusbInit(null);
```

Generated code supports both static entity methods and optional global PHP functions, controlled by the `features.use_functions` configuration setting.

> **Status:** pnl is an early implementation. Local path, `file://`, and git-based installations work today. Repository index solving, signed package indexes, and FTP downloads are still in design.
