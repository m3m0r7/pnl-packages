# libpixman/libpixman examples

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
