# SRT Package

Package: `libsrt/libsrt`

Base library: SRT

License: MPL-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsrt
```

The package requires the SRT headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libsrt\Libsrt;

// srt_getversion() returns the version packed as 0xMMmmpp.
$v = Libsrt::srt_getversion()->toInt();
printf("srt %d.%d.%d\n", ($v >> 16) & 0xff, ($v >> 8) & 0xff, $v & 0xff);
```

This snippet is printed when `pnl install libsrt` finishes — it comes from the
package's `examples` field in `pnlx.json`.
