# libssh2 Package

Package: `libssh2/libssh2`

Base library: libssh2

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libssh2
```

The package requires libssh2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libssh2\Libssh2;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libssh2 = $runtime->load(Libssh2::class);

// Print the libssh2 version string.
echo $libssh2->libssh2_version(0) . PHP_EOL;

// Initialise the library (call once at application start).
$libssh2->libssh2_init(0);

// Create a session for a connected socket $sock (int):
// $session = $libssh2->libssh2_session_init_ex(null, null, null, null);
// if (!is_null($session)) { $libssh2->libssh2_session_handshake($session, $sock); }
$libssh2->libssh2_exit();
```

This snippet is printed when `pnl install libssh2` finishes — it comes from the package's `examples` field in `pnlx.json`.
