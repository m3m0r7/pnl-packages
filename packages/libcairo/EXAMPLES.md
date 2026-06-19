# libcairo/libcairo examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcairo\Libcairo;
use function Pnlx\Util\is_null;

// Draw a red circle on a PNG image surface and save it
$surface = Libcairo::cairo_image_surface_create(
    0,    // CAIRO_FORMAT_ARGB32
    200, 200
);
if (is_null($surface)) {
    throw new \RuntimeException('cairo_image_surface_create failed');
}
$cr = Libcairo::cairo_create($surface);
Libcairo::cairo_set_source_rgb($cr, 1.0, 0.0, 0.0); // red
Libcairo::cairo_arc($cr, 100.0, 100.0, 80.0, 0.0, 2 * M_PI);
Libcairo::cairo_fill($cr);
Libcairo::cairo_surface_write_to_png($surface, 'circle.png');
Libcairo::cairo_destroy($cr);
Libcairo::cairo_surface_destroy($surface);
```
