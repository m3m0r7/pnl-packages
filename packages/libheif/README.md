# libheif Package

Package: `libheif/libheif`

Base library: libheif

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libheif
```

The package requires libheif headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libheif\Libheif;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libheif = $runtime->load(Libheif::class);

// Query libheif version string
$version = $libheif->heif_get_version();
echo "libheif version: " . $version . "\n";

// Allocate a context, load a HEIF file, then release
$ctx = $libheif->heif_context_alloc();
if (!is_null($ctx)) {
    // $err = $libheif->heif_context_read_from_file($ctx, 'image.heic', null);
    $libheif->heif_context_free($ctx);
}
```

This snippet is printed when `pnl install libheif` finishes — it comes from the package's `examples` field in `pnlx.json`.
