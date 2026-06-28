# libpopt file-sanity check

`poptSaneFile()` reports whether a path is a "sane" config file: a regular file, owned by you or root, and not group- or world-writable.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpopt\Libpopt;

// poptSaneFile() reports whether a path is a "sane" config file: a regular
// file, owned by you or root, and not group- or world-writable. Returns 1/0.
$sane = Libpopt::poptSaneFile(__FILE__);
$sane = is_object($sane) ? $sane->toInt() : $sane;
echo 'this script is sane: ' . ($sane ? 'yes' : 'no') . "\n";

$missing = Libpopt::poptSaneFile('/no/such/file');
$missing = is_object($missing) ? $missing->toInt() : $missing;
echo 'missing file is sane: ' . ($missing ? 'yes' : 'no') . "\n";
```
