# libvips/libvips examples

```php
use Pnlx\Libvips\Libvips;

$libvips = new Libvips();

// vips_init(argv0) must run once before any other vips call.
$libvips->vips_init('pnl');
$major = $libvips->vips_version(0);
echo "libvips major: $major\n";
$libvips->vips_shutdown();

// Explore further: vips_image_new_from_file(), vips_resize(),
// vips_thumbnail(), vips_image_write_to_file(), ...
```
