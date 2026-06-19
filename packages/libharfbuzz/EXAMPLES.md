# libharfbuzz/libharfbuzz examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libharfbuzz\Libharfbuzz;

// Query HarfBuzz version
$versionStr = Libharfbuzz::hb_version_string();
echo "HarfBuzz: " . $versionStr . "\n";

// Create a shaping buffer, add text, then destroy it
$buf = Libharfbuzz::hb_buffer_create();
Libharfbuzz::hb_buffer_add_utf8($buf, 'Hello', -1, 0, -1);
Libharfbuzz::hb_buffer_guess_segment_properties($buf);
// Shape with a font: Libharfbuzz::hb_shape($font, $buf, null, 0);
Libharfbuzz::hb_buffer_destroy($buf);
```
