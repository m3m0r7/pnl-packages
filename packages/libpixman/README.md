# Pixman Package

Package: `libpixman/libpixman`

Base library: Pixman

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libpixman
```

The package requires Pixman headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libpixman\Libpixman;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libpixman = $runtime->load(Libpixman::class);

// Query the Pixman library version
$versionStr = $libpixman->pixman_version_string();
echo "Pixman version: {$versionStr}\n";

// Composite two ARGB32 images: allocate image structs with pixman_image_create_bits(),
// then call pixman_image_composite32() to blend them, and pixman_image_unref() to free.
// Example: $src = $libpixman->pixman_image_create_bits(PIXMAN_a8r8g8b8, $w, $h, $bits, $stride);
//          $libpixman->pixman_image_composite32(PIXMAN_OP_OVER, $src, null, $dst, 0, 0, 0, 0, 0, 0, $w, $h);
//          $libpixman->pixman_image_unref($src);
```

This snippet is printed when `pnl install libpixman` finishes — it comes from the package's `examples` field in `pnlx.json`.
