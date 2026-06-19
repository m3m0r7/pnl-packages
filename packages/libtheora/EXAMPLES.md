# libtheora/libtheora examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtheora\Libtheora;

// theora_version_string() returns the Theora release string.
$version = Libtheora::theoraVersionString();
echo "libtheora: " . (string) $version . "\n";

// theora_version_number() returns the encoded version (major<<16 | minor<<8 | sub).
$number = Libtheora::theoraVersionNumber();
$encoded = (int) (string) $number;
printf(
    "version number: 0x%06x (%d.%d.%d)\n",
    $encoded,
    ($encoded >> 16) & 0xff,
    ($encoded >> 8) & 0xff,
    $encoded & 0xff
);
```
