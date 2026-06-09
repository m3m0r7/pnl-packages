# libevent Package

Package: `libevent/libevent`

Base library: libevent

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libevent
```

The package requires libevent headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libevent\Libevent;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libevent = $runtime->load(Libevent::class);

// Query the libevent version string and method (backend) name.
$version = $libevent->event_get_version();
echo "libevent version: " . $version . PHP_EOL;

// Create a default event_base (uses best available backend).
$base = $libevent->event_base_new();
if (is_null($base)) {
    throw new \RuntimeException('event_base_new() failed');
}
$method = $libevent->event_base_get_method($base);
echo "Backend method: " . $method . PHP_EOL;

$libevent->event_base_free($base);
```

This snippet is printed when `pnl install libevent` finishes — it comes from the package's `examples` field in `pnlx.json`.
