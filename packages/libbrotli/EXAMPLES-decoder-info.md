# libbrotli decoder version and error strings

Read the decoder library version and turn a decoder error code into a readable message.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libbrotli\Libbrotli;

// Decoder library version (packed MAJOR<<24 | MINOR<<12 | PATCH).
$raw = Libbrotli::BrotliDecoderVersion();
$v   = is_object($raw) ? $raw->toInt() : $raw;
printf("Brotli decoder %d.%d.%d\n", ($v >> 24) & 0xff, ($v >> 12) & 0xfff, $v & 0xfff);

// Human-readable message for a decoder error code (0 = no error).
echo "error 0: " . (string) Libbrotli::BrotliDecoderErrorString(0) . "\n";
```
