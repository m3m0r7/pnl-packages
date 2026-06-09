# libuv Package

Package: `libuv/libuv`

Base library: libuv

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libuv
```

The package requires libuv headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libuv\Libuv;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libuv = $runtime->load(Libuv::class);

// Print the libuv version string and numeric version.
echo $libuv->uv_version_string() . PHP_EOL; // e.g. '1.48.0'
echo $libuv->uv_version() . PHP_EOL;        // packed int: major<<16|minor<<8|patch

// Get (or create) the default event loop and run it.
$loop = $libuv->uv_default_loop();
// Attach handles/requests to $loop here, then:
$libuv->uv_run($loop, 0 /* UV_RUN_DEFAULT */);
$libuv->uv_loop_close($loop);
```

This snippet is printed when `pnl install libuv` finishes — it comes from the package's `examples` field in `pnlx.json`.
