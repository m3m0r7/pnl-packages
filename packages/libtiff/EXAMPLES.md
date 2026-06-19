# libtiff/libtiff examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtiff\Libtiff;

// TIFFGetVersion() returns the multi-line version banner; no file needed.
echo strtok((string) Libtiff::TIFFGetVersion(), "\n") . "\n"; // e.g. "LIBTIFF, Version 4.x"
```
