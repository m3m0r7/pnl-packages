# libsamplerate/libsamplerate converter info

Inspect converter descriptions and validate sample-rate ratios using pure lookup and validation calls that need no resampler state.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsamplerate\Libsamplerate;

// Inspect converter metadata and validate sample-rate ratios — pure lookup and
// validation calls that need no resampler state.
for ($type = 0; $type <= 2; $type++) {
    echo "converter {$type}: " . (string) Libsamplerate::src_get_description($type) . "\n";
}

foreach ([2.0, 0.5, 0.0, -1.0] as $ratio) {
    $valid = Libsamplerate::src_is_valid_ratio($ratio);
    $valid = is_object($valid) ? $valid->toInt() : $valid;
    echo "ratio {$ratio} valid? " . ($valid ? 'yes' : 'no') . "\n";
}
```
