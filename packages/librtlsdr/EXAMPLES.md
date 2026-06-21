# librtlsdr/librtlsdr examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Librtlsdr\Librtlsdr;
use function Pnlx\Util\is_null;

// List all connected RTL-SDR devices
$count = Librtlsdr::rtlsdr_get_device_count()->toInt();
echo "RTL-SDR devices found: {$count}\n";
for ($i = 0; $i < $count; $i++) {
    $name = Librtlsdr::rtlsdr_get_device_name($i);
    echo "  [{$i}] {$name}\n";
}

// Open the first device and tune to FM broadcast band
if ($count > 0) {
    // rtlsdr_open takes an `rtlsdr_dev_t **` out-parameter, so pass a variable by
    // reference: the call writes the device handle back into $dev (used directly).
    $dev = null;
    Librtlsdr::rtlsdr_open($dev, 0);
    Librtlsdr::rtlsdr_set_center_freq($dev, 98_000_000); // 98 MHz
    Librtlsdr::rtlsdr_set_sample_rate($dev, 2_048_000);  // 2.048 MS/s
    // Librtlsdr::rtlsdr_read_sync($dev, $buf, $len, $nRead)
    Librtlsdr::rtlsdr_close($dev);
}
```
