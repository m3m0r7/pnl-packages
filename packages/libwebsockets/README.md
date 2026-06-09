# libwebsockets Package

Package: `libwebsockets/libwebsockets`

Base library: libwebsockets

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libwebsockets
```

The package requires libwebsockets headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libwebsockets\Libwebsockets;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libwebsockets = $runtime->load(Libwebsockets::class);

// lws_get_library_version() returns the version string, e.g. "4.3.3".
$version = $libwebsockets->lws_get_library_version();
echo "libwebsockets version: $version\n";

// Explore further: lws_create_context(), lws_client_connect_via_info(),
// lws_service(), lws_context_destroy(), ...
```

This snippet is printed when `pnl install libwebsockets` finishes — it comes from the package's `examples` field in `pnlx.json`.
