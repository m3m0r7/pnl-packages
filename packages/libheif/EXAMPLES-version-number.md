# libheif numeric version

Read the libheif version as individual numeric components and as a single packed comparable integer.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libheif\Libheif;

$n = fn($x) => is_object($x) ? $x->toInt() : $x;

// Read the libheif version as individual numeric components.
$major = $n(Libheif::heif_get_version_number_major());
$minor = $n(Libheif::heif_get_version_number_minor());
$patch = $n(Libheif::heif_get_version_number_maintenance());
echo "libheif numeric version: {$major}.{$minor}.{$patch}\n";

// The same version packed into a single comparable integer (0xMMNNPPxx).
$packed = $n(Libheif::heif_get_version_number());
echo "packed version number: {$packed}\n";
```
