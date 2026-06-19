# libjxl/libjxl examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libjxl\Libjxl;

// JxlDecoderVersion() returns the encoded version, e.g. 10002 for 0.10.2.
$version = Libjxl::JxlDecoderVersion();
echo "libjxl version code: $version\n";

// Explore further: JxlDecoderCreate(), JxlDecoderProcessInput(),
// JxlEncoderCreate(), JxlEncoderAddImageFrame(), ...
```
