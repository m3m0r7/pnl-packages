# libaom/libaom build info example

Read the numeric codec version and the configure-time build configuration of the linked libaom.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libaom\Libaom;

// aom_codec_version() returns the packed numeric codec version.
$v = Libaom::aom_codec_version();
echo 'version number: ' . (is_object($v) ? $v->toInt() : $v) . PHP_EOL;

// aom_codec_build_config() returns the configure-time build configuration string.
echo 'build config: ' . (string) Libaom::aom_codec_build_config() . PHP_EOL;
```
