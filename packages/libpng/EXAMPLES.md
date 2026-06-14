# libpng/libpng examples

```php
use Pnlx\Libpng\Libpng;
use function Pnlx\Util\is_null;

// Print the runtime libpng version string
$versionNum = Libpng::png_access_version_number();
echo "libpng version number: {$versionNum}\n"; // e.g. 10643

// Read a PNG file: create read struct, set up I/O, then call png_read_image()
$png = Libpng::png_create_read_struct('1.6.43', null, null, null);
if (is_null($png)) {
    throw new \RuntimeException('png_create_read_struct failed');
}
$info = Libpng::png_create_info_struct($png);
// Libpng::png_init_io($png, $fp);
// Libpng::png_read_info($png, $info);
// $width  = Libpng::png_get_image_width($png, $info);
// $height = Libpng::png_get_image_height($png, $info);
Libpng::png_destroy_read_struct($png, $info, null);
```
