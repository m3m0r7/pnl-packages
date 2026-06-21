# LAME Package

Package: `liblame/liblame`

Base library: LAME (MP3 encoder)

License: LGPL-2.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liblame
```

The package requires the LAME headers and the `libmp3lame` shared library to be
available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Liblame\Liblame;

$gf = Liblame::lame_init();
echo ($gf === null ? "lame_init failed" : "lame initialized") . PHP_EOL;
Liblame::lame_close($gf);
```

This snippet is printed when `pnl install liblame` finishes — it comes from the
package's `examples` field in `pnlx.json`.
