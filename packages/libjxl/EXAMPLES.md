# libjxl/libjxl examples

```php
use Pnlx\Libjxl\Libjxl;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libjxl = $runtime->load(Libjxl::class);

// JxlDecoderVersion() returns the encoded version, e.g. 10002 for 0.10.2.
$version = $libjxl->JxlDecoderVersion();
echo "libjxl version code: $version\n";

// Explore further: JxlDecoderCreate(), JxlDecoderProcessInput(),
// JxlEncoderCreate(), JxlEncoderAddImageFrame(), ...
```
