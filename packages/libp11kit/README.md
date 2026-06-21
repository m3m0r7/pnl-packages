# Libp11kit Package

Package: `libp11kit/libp11kit`

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libp11kit
```

## PHP usage

```php
use Pnlx\Libp11kit\Libp11kit;

// p11_kit_check_version() returns 1 when the runtime p11-kit is at least the
// requested (major, minor, micro) version, otherwise 0.
echo Libp11kit::p11_kit_check_version(0, 0, 0) . PHP_EOL; // 1
```
