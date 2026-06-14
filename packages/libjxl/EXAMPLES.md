# libjxl/libjxl examples

```php
use Pnlx\Libjxl\Libjxl;

$libjxl = new Libjxl();

// JxlDecoderVersion() returns the encoded version, e.g. 10002 for 0.10.2.
$version = $libjxl->JxlDecoderVersion();
echo "libjxl version code: $version\n";

// Explore further: JxlDecoderCreate(), JxlDecoderProcessInput(),
// JxlEncoderCreate(), JxlEncoderAddImageFrame(), ...
```
