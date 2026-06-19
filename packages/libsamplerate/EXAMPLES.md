# libsamplerate/libsamplerate examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsamplerate\Libsamplerate;
use function Pnlx\Util\is_null;

// Print library version and available converter names
echo Libsamplerate::src_get_version() . "\n";
echo Libsamplerate::src_get_name(0) . "\n"; // SRC_SINC_BEST_QUALITY

// Create a resampler (SRC_LINEAR = 2), 1 channel. The int error code is an
// out-parameter: pass a plain variable by reference.
$errCode = 0;
$state = Libsamplerate::src_new(2, 1, $errCode);
if (is_null($state)) {
    throw new \RuntimeException('src_new failed: ' . Libsamplerate::src_strerror($errCode));
}

// Convert: fill an SRC_DATA struct, then Libsamplerate::src_process($state, $srcData)
// Ratio example — 44100 Hz -> 22050 Hz: $srcData->src_ratio = 0.5

Libsamplerate::src_delete($state);
echo "Resampler created and deleted\n";
```
