# libnng/libnng runtime utilities

Decode an NNG error code, draw a strong random 32-bit integer, and read the millisecond monotonic clock.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnng\Libnng;

// nng_strerror() maps an NNG error code to a human-readable message.
$msg = Libnng::nng_strerror(5); // NNG_ETIMEDOUT
echo 'strerror(5): ' . (string)$msg . "\n"; // Timed out

// nng_random() returns a cryptographically strong random 32-bit unsigned integer.
$rand = Libnng::nng_random();
echo 'random: ' . (is_object($rand) ? $rand->toInt() : $rand) . "\n";

// nng_clock() returns a millisecond timestamp from an arbitrary epoch.
$clock = Libnng::nng_clock();
echo 'clock: ' . (is_object($clock) ? $clock->toInt() : $clock) . "\n";
```
