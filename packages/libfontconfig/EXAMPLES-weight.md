# libfontconfig weight conversion

Convert font weights between the OpenType scale (100-900) and fontconfig's internal scale.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfontconfig\Libfontconfig;

// FcWeightFromOpenType() maps an OpenType weight (100-900) to fontconfig's scale.
$fc = Libfontconfig::FcWeightFromOpenType(400);
$fc = is_object($fc) ? $fc->toInt() : $fc;
echo "OpenType 400 (Regular) -> fontconfig weight $fc\n";

// FcWeightToOpenType() is the inverse mapping.
$ot = Libfontconfig::FcWeightToOpenType($fc);
$ot = is_object($ot) ? $ot->toInt() : $ot;
echo "fontconfig $fc -> OpenType weight $ot\n";
```
