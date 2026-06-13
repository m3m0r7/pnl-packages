# libsixel/libsixel examples

```php
use Pnlx\Libsixel\Libsixel;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libsixel = $runtime->load(Libsixel::class);

// Grab the built-in xterm 256-colour palette (SIXEL_BUILTIN_XTERM256 = 2).
$dither = $libsixel->sixel_dither_get(2);
$libsixel->sixel_dither_unref($dither);

// Explore further: sixel_encoder_new(), sixel_encoder_encode(),
// sixel_output_new(), sixel_dither_new(), sixel_encode(), ...
```
