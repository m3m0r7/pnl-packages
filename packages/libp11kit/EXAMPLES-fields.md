# libp11kit space-padded fields and error messages

p11-kit's `p11_kit_space_strlen()` measures a fixed-width, space-padded PKCS#11 field, while `p11_kit_message()` reports the most recent error on the current thread.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libp11kit\Libp11kit;

// p11_kit_space_strlen() measures a PKCS#11 fixed-width, space-padded field,
// returning the visible length with trailing spaces trimmed.
$padded = 'TOKEN LABEL         '; // 20-byte field
$len = Libp11kit::p11_kit_space_strlen($padded, strlen($padded));
echo (is_object($len) ? $len->toInt() : $len) . PHP_EOL; // 11

// p11_kit_message() returns the most recent p11-kit error string for the
// current thread, or null when nothing has failed yet.
$msg = Libp11kit::p11_kit_message();
echo ($msg === null ? '(no error)' : (string) $msg) . PHP_EOL;
```
