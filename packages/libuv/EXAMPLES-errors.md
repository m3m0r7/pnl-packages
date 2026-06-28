# libuv error code lookups

Translate a libuv error code into its symbolic name with `uv_err_name()` and into a human-readable message with `uv_strerror()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libuv\Libuv;

// uv_err_name() maps a libuv error code to its symbolic name and uv_strerror()
// returns the human-readable message. Both take the negative integer code.
$einval = -22; // UV_EINVAL
echo (string) Libuv::uv_err_name($einval) . PHP_EOL;  // EINVAL
echo (string) Libuv::uv_strerror($einval) . PHP_EOL;  // invalid argument

$enoent = -2; // UV_ENOENT
echo (string) Libuv::uv_err_name($enoent) . PHP_EOL;  // ENOENT
echo (string) Libuv::uv_strerror($enoent) . PHP_EOL;  // no such file or directory
```
