# libogg bitpacker

Use the Oggpack bitpacker to write arbitrary-width fields and read back how many bits and bytes were packed.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libogg\Libogg;
use Pnlx\Libogg\Types\oggpack_buffer;

// The Oggpack bitpacker writes arbitrary-width fields into a growing buffer.
$b = new oggpack_buffer();
Libogg::oggpack_writeinit($b);
Libogg::oggpack_write($b, 5, 8);    // 8-bit field
Libogg::oggpack_write($b, 300, 16); // 16-bit field

$bits = Libogg::oggpack_bits($b);
$bits = is_object($bits) ? $bits->toInt() : $bits;
$bytes = Libogg::oggpack_bytes($b);
$bytes = is_object($bytes) ? $bytes->toInt() : $bytes;
echo "packed bits=$bits bytes=$bytes\n"; // packed bits=24 bytes=3

Libogg::oggpack_writeclear($b);
```
