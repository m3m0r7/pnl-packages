# libtheora th_* version API

The modern `th_*` API reports the build with `th_version_string()` and a packed numeric version with `th_version_number()` (`major<<16 | minor<<8 | sub`).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtheora\Libtheora;

// th_version_string() returns the libtheora 1.x release string.
$s = Libtheora::thVersionString();
echo "th_version_string: " . (string) $s . "\n";

// th_version_number() returns the packed version (major<<16 | minor<<8 | sub).
$n = Libtheora::thVersionNumber();
$encoded = is_object($n) ? $n->toInt() : $n;
printf(
    "th_version_number: 0x%06x (%d.%d.%d)\n",
    $encoded,
    ($encoded >> 16) & 0xff,
    ($encoded >> 8) & 0xff,
    $encoded & 0xff
);
```
