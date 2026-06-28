# libcfitsio network timeout

Read the current network (HTTP/FTP) read timeout that CFITSIO uses for remote FITS files.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcfitsio\Libcfitsio;

// ffgtmo() returns the current network (HTTP/FTP) read timeout in seconds.
$timeout = Libcfitsio::ffgtmo();
echo 'cfitsio network timeout (s): ' . (is_object($timeout) ? $timeout->toInt() : $timeout) . "\n";
```
