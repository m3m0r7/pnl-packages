# libgcrypt/libgcrypt examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgcrypt\Libgcrypt;

// gcry_check_version(null) initialises libgcrypt and returns its version string.
echo "libgcrypt " . Libgcrypt::gcry_check_version(null) . "\n";
```
