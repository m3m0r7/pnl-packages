# GNU Aspell Package

Package: `libaspell/libaspell`

Base library: GNU Aspell

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libaspell
```

The package requires the GNU Aspell headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libaspell\Libaspell;

// aspell_version_string() returns the GNU Aspell version string.
echo Libaspell::aspell_version_string() . PHP_EOL;
```

This snippet is printed when `pnl install libaspell` finishes — it comes from the
package's `examples` field in `pnlx.json`.
