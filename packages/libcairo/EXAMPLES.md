# libcairo/libcairo examples

```php
use Pnlx\Libcairo\Libcairo;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libcairo = $runtime->load(Libcairo::class);

// Draw a red circle on a PNG image surface and save it
$surface = $libcairo->cairo_image_surface_create(
    0,    // CAIRO_FORMAT_ARGB32
    200, 200
);
if (is_null($surface)) {
    throw new \RuntimeException('cairo_image_surface_create failed');
}
$cr = $libcairo->cairo_create($surface);
$libcairo->cairo_set_source_rgb($cr, 1.0, 0.0, 0.0); // red
$libcairo->cairo_arc($cr, 100.0, 100.0, 80.0, 0.0, 2 * M_PI);
$libcairo->cairo_fill($cr);
$libcairo->cairo_surface_write_to_png($surface, 'circle.png');
$libcairo->cairo_destroy($cr);
$libcairo->cairo_surface_destroy($surface);
```
