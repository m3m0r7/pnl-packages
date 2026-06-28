# libopus/libopus error messages

Translate Opus error codes into human-readable strings with `opus_strerror()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libopus\Libopus;

// opus_strerror() maps an Opus error code to its human-readable message.
// OPUS_OK = 0, OPUS_BAD_ARG = -1, OPUS_INVALID_PACKET = -4, OPUS_UNIMPLEMENTED = -5.
foreach ([0, -1, -4, -5] as $code) {
    $msg = Libopus::opus_strerror($code);
    echo "opus_strerror($code) = " . (string)$msg . "\n";
}
```
