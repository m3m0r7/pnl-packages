# Opus Package

Package: `libopus/libopus`

Base library: Opus

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libopus
```

The package requires Opus headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libopus\Libopus;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libopus = $runtime->load(Libopus::class);

// Query the library version string (char* → PHP string)
$version = $libopus->opus_get_version_string();
echo "Opus version: $version\n";

// Create an encoder: 48 kHz, 2 channels, OPUS_APPLICATION_AUDIO = 2049
$error = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$encoder = $libopus->opus_encoder_create(48000, 2, 2049, $error);
if (is_null($encoder)) {
    echo "Encoder error: " . $error->cdata . "\n";
} else {
    // ... encode PCM frames with opus_encode() ...
    $libopus->opus_encoder_destroy($encoder);
}
```

This snippet is printed when `pnl install libopus` finishes — it comes from the package's `examples` field in `pnlx.json`.
