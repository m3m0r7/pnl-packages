# libsamplerate Package

Package: `libsamplerate/libsamplerate`

Base library: libsamplerate

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsamplerate
```

The package requires libsamplerate headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libsamplerate\Libsamplerate;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libsamplerate = $runtime->load(Libsamplerate::class);

// Print library version and available converter names
echo $libsamplerate->src_get_version() . "\n";
echo $libsamplerate->src_get_name(0) . "\n"; // SRC_SINC_BEST_QUALITY

// Create a resampler (SRC_LINEAR = 2), 1 channel
$errCode = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$state = $libsamplerate->src_new(2, 1, $errCode);
if (is_null($state)) {
    throw new \RuntimeException('src_new failed: ' . $libsamplerate->src_strerror($errCode[0]));
}

// Convert: fill an SRC_DATA struct, then $libsamplerate->src_process($state, $srcData)
// Ratio example — 44100 Hz -> 22050 Hz: $srcData->src_ratio = 0.5

$libsamplerate->src_delete($state);
```

This snippet is printed when `pnl install libsamplerate` finishes — it comes from the package's `examples` field in `pnlx.json`.
