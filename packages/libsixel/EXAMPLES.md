# libsixel/libsixel examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsixel\Libsixel;

// Grab the built-in xterm 256-colour palette (SIXEL_BUILTIN_XTERM256 = 2).
$dither = Libsixel::sixel_dither_get(2);
Libsixel::sixel_dither_unref($dither);

// Explore further: sixel_encoder_new(), sixel_encoder_encode(),
// sixel_output_new(), sixel_dither_new(), sixel_encode(), ...
```
