# libopus/libopus examples

```php
use Pnlx\Libopus\Libopus;
use function Pnlx\Util\is_null;

// Query the library version string (char* → PHP string)
$version = Libopus::opus_get_version_string();
echo "Opus version: $version\n";

// Create an encoder: 48 kHz, 2 channels, OPUS_APPLICATION_AUDIO = 2049
$error = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$encoder = Libopus::opus_encoder_create(48000, 2, 2049, $error);
if (is_null($encoder)) {
    echo "Encoder error: " . $error->cdata . "\n";
} else {
    // ... encode PCM frames with opus_encode() ...
    Libopus::opus_encoder_destroy($encoder);
}
```
