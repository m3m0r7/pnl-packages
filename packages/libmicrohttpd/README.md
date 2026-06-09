# GNU libmicrohttpd Package

Package: `libmicrohttpd/libmicrohttpd`

Base library: GNU libmicrohttpd

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmicrohttpd
```

The package requires GNU libmicrohttpd headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmicrohttpd\Libmicrohttpd;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libmicrohttpd = $runtime->load(Libmicrohttpd::class);

// Query the libmicrohttpd runtime version string.
$ver = $libmicrohttpd->MHD_get_version(); // returns string, e.g. "0.9.77"
echo 'libmicrohttpd version: ' . $ver . PHP_EOL;
// Main entry point to explore: MHD_start_daemon() — starts an embedded HTTP
// server on a given port with a request-handler callback, returns MHD_Daemon*.
```

This snippet is printed when `pnl install libmicrohttpd` finishes — it comes from the package's `examples` field in `pnlx.json`.
