# libimagequant attribute tuning

Create a quantization attribute object, read its built-in defaults, and adjust the palette size before discarding it.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libimagequant\Libimagequant;

// Create a quantization attribute, inspect its defaults, then tune it.
$attr = Libimagequant::liq_attr_create();

$maxColors = Libimagequant::liq_get_max_colors($attr);
echo 'default max colors: ' . (is_object($maxColors) ? $maxColors->toInt() : $maxColors) . PHP_EOL;

$speed = Libimagequant::liq_get_speed($attr);
echo 'default speed: ' . (is_object($speed) ? $speed->toInt() : $speed) . PHP_EOL;

Libimagequant::liq_set_max_colors($attr, 64);
$tuned = Libimagequant::liq_get_max_colors($attr);
echo 'tuned max colors: ' . (is_object($tuned) ? $tuned->toInt() : $tuned) . PHP_EOL;

Libimagequant::liq_attr_destroy($attr);
```
