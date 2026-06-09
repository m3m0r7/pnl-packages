# libexif Package

Package: `libexif/libexif`

Base library: libexif

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libexif
```

The package requires libexif headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libexif\Libexif;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libexif = $runtime->load(Libexif::class);

// Load EXIF data from a JPEG file.
$data = $libexif->exif_data_new_from_file('/path/to/photo.jpg');
if (is_null($data)) {
    echo "No EXIF data found." . PHP_EOL;
} else {
    // Dump all tags to stdout (uses the library's own formatter).
    $libexif->exif_data_dump($data);
    $libexif->exif_data_unref($data);
}

// exif_data_new_from_data() can parse raw bytes from a variable instead.
```

This snippet is printed when `pnl install libexif` finishes — it comes from the package's `examples` field in `pnlx.json`.
