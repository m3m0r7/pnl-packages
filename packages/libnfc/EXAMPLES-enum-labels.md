# libnfc baud rate and modulation labels

Turn `nfc_baud_rate` and `nfc_modulation_type` enum values into human-readable labels with the pure `str_nfc_baud_rate()` and `str_nfc_modulation_type()` helpers (no device required).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnfc\Libnfc;

// str_nfc_baud_rate() turns an nfc_baud_rate enum value into a label.
foreach ([1, 2, 3, 4] as $nbr) {
    echo "baud $nbr: " . (string)Libnfc::str_nfc_baud_rate($nbr) . "\n";
}

// str_nfc_modulation_type() turns an nfc_modulation_type enum value into a label.
foreach ([1, 7, 8] as $nmt) {
    echo "modulation $nmt: " . (string)Libnfc::str_nfc_modulation_type($nmt) . "\n";
}
```
