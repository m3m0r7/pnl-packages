# libpixman/libpixman version and format-support example

Read the numeric library version and ask whether a given pixel format can be used as a compositing destination.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpixman\Libpixman;
use const Pnlx\Libpixman\PIXMAN_a8r8g8b8;

// pixman_version() returns the numeric (encoded) library version.
$v = Libpixman::pixman_version();
echo "Pixman numeric version: " . (is_object($v) ? $v->toInt() : $v) . "\n";

// pixman_format_supported_destination() reports whether the linked build can use
// a given pixel format as a compositing destination.
$ok = Libpixman::pixman_format_supported_destination(PIXMAN_a8r8g8b8);
$ok = is_object($ok) ? $ok->toInt() : $ok;
echo "a8r8g8b8 usable as destination: " . ($ok ? "yes" : "no") . "\n";
```
