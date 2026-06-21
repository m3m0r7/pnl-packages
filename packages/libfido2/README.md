# Libfido2 Package

Package: `libfido2/libfido2`

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libfido2
```

## PHP usage

```php
use Pnlx\Libfido2\Libfido2;

// fido_strerr() maps a libfido2 status code to its message string.
echo Libfido2::fido_strerr(0) . PHP_EOL; // "FIDO_ERR_SUCCESS"
```
