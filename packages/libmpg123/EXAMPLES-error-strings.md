# libmpg123/libmpg123 error strings and encoding sizes

Look up human-readable messages for mpg123 error codes and the byte size of an audio encoding without opening a decoder handle.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmpg123\Libmpg123;

// mpg123_plain_strerror() turns an error code into a human-readable message.
$err0 = Libmpg123::mpg123_plain_strerror(0);
echo "errcode 0: " . (string)$err0 . "\n"; // No error... (code 0)

$err1 = Libmpg123::mpg123_plain_strerror(1);
echo "errcode 1: " . (string)$err1 . "\n"; // Unable to set up output format! (code 1)

// mpg123_encsize() returns the byte size per sample of an encoding
// (208 == MPG123_ENC_SIGNED_16).
$size = Libmpg123::mpg123_encsize(208);
echo "encsize(SIGNED_16) bytes/sample: " . (is_object($size) ? $size->toInt() : $size) . "\n"; // 2
```
