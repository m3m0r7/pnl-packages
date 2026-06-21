# Little-CMS Package

Package: `liblcms2/liblcms2`

Base library: Little-CMS

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liblcms2
```

The package requires the Little-CMS headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Liblcms2\Liblcms2;

// cmsGetEncodedCMMversion() returns the Little-CMS version encoded as MMmm0.
$v = Liblcms2::cmsGetEncodedCMMversion()->toInt();
printf("lcms2 %.2f\n", $v / 1000);
```

This snippet is printed when `pnl install liblcms2` finishes — it comes from the
package's `examples` field in `pnlx.json`.
