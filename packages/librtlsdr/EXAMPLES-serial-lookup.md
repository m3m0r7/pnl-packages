# librtlsdr/librtlsdr serial lookup

Resolve a device index from its USB serial string without opening any device or touching hardware.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Librtlsdr\Librtlsdr;

// Resolve a device index from its USB serial string without opening any device
// or touching hardware. The call returns the matching index, or a negative
// error code (e.g. -2 when no RTL-SDR devices are present).
foreach (['00000001', 'missing-serial'] as $serial) {
    $idx = Librtlsdr::rtlsdr_get_index_by_serial($serial);
    $idx = is_object($idx) ? $idx->toInt() : $idx;
    echo "serial '{$serial}' => index {$idx}\n";
}
```
