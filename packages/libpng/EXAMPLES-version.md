# libpng/libpng version & copyright

Query libpng's build version and copyright strings without creating any read/write struct, since these accessors take a `png_const_structrp` that may be NULL.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpng\Libpng;

// libpng's version/copyright accessors take a png_const_structrp that may be
// NULL, so they can be queried without creating any read/write struct.
// Each returns a string (wrapped values cast cleanly with (string)).
$libpngVer = (string) Libpng::png_get_libpng_ver(null);
$headerVer = (string) Libpng::png_get_header_version(null);
$copyright = (string) Libpng::png_get_copyright(null);

echo "libpng version: {$libpngVer}\n";
echo "header version: " . trim($headerVer) . "\n";
echo "copyright:\n{$copyright}\n";
```
