# libpng Package

Package: `libpng/libpng`

Base library: libpng

License: libpng-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libpng
```

The package requires libpng headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libpng\Libpng;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libpng = $runtime->load(Libpng::class);

// Print the runtime libpng version string
$versionNum = $libpng->png_access_version_number();
echo "libpng version number: {$versionNum}\n"; // e.g. 10643

// Read a PNG file: create read struct, set up I/O, then call png_read_image()
$png = $libpng->png_create_read_struct('1.6.43', null, null, null);
if (is_null($png)) {
    throw new \RuntimeException('png_create_read_struct failed');
}
$info = $libpng->png_create_info_struct($png);
// $libpng->png_init_io($png, $fp);
// $libpng->png_read_info($png, $info);
// $width  = $libpng->png_get_image_width($png, $info);
// $height = $libpng->png_get_image_height($png, $info);
$libpng->png_destroy_read_struct($png, $info, null);
```

This snippet is printed when `pnl install libpng` finishes — it comes from the package's `examples` field in `pnlx.json`.
