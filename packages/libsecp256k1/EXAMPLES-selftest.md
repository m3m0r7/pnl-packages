# libsecp256k1/libsecp256k1 self-test example

Run the library's built-in consistency checks with `secp256k1_selftest()`, which needs no context, keys or buffers and aborts the process on failure, so reaching the next line confirms the build is sound.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsecp256k1\Libsecp256k1;

// secp256k1_selftest() runs the library's internal consistency checks. It needs
// no context, no keys and no buffers; on failure libsecp256k1 aborts the
// process, so reaching the line after the call means the build is sound.
Libsecp256k1::secp256k1_selftest();
echo 'libsecp256k1 self-test passed', PHP_EOL;
```
