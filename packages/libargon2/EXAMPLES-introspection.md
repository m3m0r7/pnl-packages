# libargon2/libargon2 introspection examples

`argon2_error_message` turns an Argon2 error code into a human-readable string and `argon2_encodedlen` computes the length of the encoded hash string for the given parameters.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libargon2\Libargon2;

// argon2_error_message maps an Argon2 status code to its message (0 = ARGON2_OK).
echo (string)Libargon2::argon2_error_message(0) . "\n";  // OK
echo (string)Libargon2::argon2_error_message(-1) . "\n"; // Output pointer is NULL

// argon2_encodedlen(t_cost, m_cost, parallelism, saltlen, hashlen, type) returns
// the number of bytes needed to hold the encoded hash string (type 2 = Argon2id).
$len = Libargon2::argon2_encodedlen(2, 65536, 1, 16, 32, 2);
echo (is_object($len) ? $len->toInt() : $len) . "\n"; // 98
```
