# libopus/libopus examples

```php
use Pnlx\Libopus\Libopus;
use function Pnlx\Util\is_null;

// Query the library version string (char* → PHP string)
$version = Libopus::opus_get_version_string();
echo "Opus version: $version\n";

// Create an encoder: 48 kHz, 2 channels, OPUS_APPLICATION_AUDIO = 2049. The int
// error code is an out-parameter: pass a plain variable by reference.
$error = 0;
$encoder = Libopus::opus_encoder_create(48000, 2, 2049, $error);
if (is_null($encoder)) {
    echo "Encoder error: {$error}\n";
} else {
    // ... encode PCM frames with opus_encode() ...
    Libopus::opus_encoder_destroy($encoder);
    echo "Encoder created and destroyed\n";
}
```
