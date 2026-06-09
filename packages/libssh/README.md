# libssh Package

Package: `libssh/libssh`

Base library: libssh

License: LGPL-2.1-only

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libssh
```

The package requires libssh headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libssh\Libssh;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libssh = $runtime->load(Libssh::class);

// Create a new SSH session.
$session = $libssh->ssh_new();
if (is_null($session)) { throw new \RuntimeException('ssh_new failed'); }

// Configure the host before connecting.
$libssh->ssh_options_set($session, 0 /* SSH_OPTIONS_HOST */, 'example.com');

// Connect, authenticate, run commands, then free the session.
// $libssh->ssh_connect($session);
$libssh->ssh_free($session);
```

This snippet is printed when `pnl install libssh` finishes — it comes from the package's `examples` field in `pnlx.json`.
