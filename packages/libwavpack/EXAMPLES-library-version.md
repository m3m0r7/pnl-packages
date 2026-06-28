# libwavpack/libwavpack library version (numeric)

`WavpackGetLibraryVersion()` returns the linked library version packed into a 32-bit integer as `0x00MMmmpp` (major/minor/patch), complementing the human-readable string form.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libwavpack\Libwavpack;

// WavpackGetLibraryVersion() returns the version packed as 0x00MMmmpp (major/minor/patch).
$v = Libwavpack::WavpackGetLibraryVersion();
$v = is_object($v) ? $v->toInt() : $v;
echo sprintf("WavPack library version: %d.%d.%d (0x%06x)\n",
    ($v >> 16) & 0xff, ($v >> 8) & 0xff, $v & 0xff, $v);
```
