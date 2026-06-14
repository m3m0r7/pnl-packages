# libsamplerate/libsamplerate examples

```php
use Pnlx\Libsamplerate\Libsamplerate;
use function Pnlx\Util\is_null;

$libsamplerate = new Libsamplerate();

// Print library version and available converter names
echo $libsamplerate->src_get_version() . "\n";
echo $libsamplerate->src_get_name(0) . "\n"; // SRC_SINC_BEST_QUALITY

// Create a resampler (SRC_LINEAR = 2), 1 channel
$errCode = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$state = $libsamplerate->src_new(2, 1, $errCode);
if (is_null($state)) {
    throw new \RuntimeException('src_new failed: ' . $libsamplerate->src_strerror($errCode[0]));
}

// Convert: fill an SRC_DATA struct, then $libsamplerate->src_process($state, $srcData)
// Ratio example — 44100 Hz -> 22050 Hz: $srcData->src_ratio = 0.5

$libsamplerate->src_delete($state);
```
