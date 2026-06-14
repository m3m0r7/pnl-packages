# libvips/libvips examples

```php
use Pnlx\Libvips\Libvips;

// vips_init(argv0) must run once before any other vips call.
Libvips::vips_init('pnl');
$major = Libvips::vips_version(0);
echo "libvips major: $major\n";
Libvips::vips_shutdown();

// Explore further: vips_image_new_from_file(), vips_resize(),
// vips_thumbnail(), vips_image_write_to_file(), ...
```
