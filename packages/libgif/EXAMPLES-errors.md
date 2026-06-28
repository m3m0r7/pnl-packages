# libgif error strings and bit sizing

Map GIFLIB error codes to messages with `GifErrorString` and compute the minimum bits needed to index a palette with `GifBitSize` — both are pure helpers needing no open file.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgif\Libgif;

// GifErrorString maps a GIFLIB error code to a human-readable message.
foreach ([1, 101, 102, 108] as $code) {
    $msg = Libgif::GifErrorString($code);
    echo "error {$code}: " . ((string)$msg) . "\n";
}

// GifBitSize returns the minimum bits needed to index n colors.
foreach ([2, 4, 16, 256] as $n) {
    $bits = Libgif::GifBitSize($n);
    echo "GifBitSize({$n}) = " . (is_object($bits) ? $bits->toInt() : $bits) . "\n";
}
```
