# libspeex bit-packing buffer

Allocate a `SpeexBits` bit-packing buffer, initialise it, and query its byte/bit counts before tearing it down.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libspeex\Libspeex;

// Allocate and initialise a SpeexBits bit-packing buffer, then query it.
$bits = new \Pnlx\Libspeex\Types\SpeexBits();
Libspeex::speex_bits_init($bits);

$nbytes = Libspeex::speex_bits_nbytes($bits);
$remaining = Libspeex::speex_bits_remaining($bits);
echo 'nbytes=' . (is_object($nbytes) ? $nbytes->toInt() : $nbytes) . PHP_EOL;
echo 'remaining=' . (is_object($remaining) ? $remaining->toInt() : $remaining) . PHP_EOL;

Libspeex::speex_bits_reset($bits);
Libspeex::speex_bits_destroy($bits);
echo 'ok' . PHP_EOL;
```
