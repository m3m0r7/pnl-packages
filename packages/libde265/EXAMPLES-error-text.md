# libde265/libde265 error text and version numbers

`de265_get_error_text()` turns a `de265_error` code into a human-readable message, while the `de265_get_version_number_*()` helpers expose the version as separate integers (distinct from the `de265_get_version()` string).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libde265\Libde265;

// de265_get_error_text() maps a de265_error code to a human-readable message.
$num = static fn($x) => is_object($x) ? $x->toInt() : $x;

echo 'DE265_OK => ' . (string) Libde265::de265_get_error_text(0) . PHP_EOL;
echo 'code 5 => ' . (string) Libde265::de265_get_error_text(5) . PHP_EOL;

// Version components as separate integers (distinct from the version string).
$maj = $num(Libde265::de265_get_version_number_major());
$min = $num(Libde265::de265_get_version_number_minor());
$mnt = $num(Libde265::de265_get_version_number_maintenance());
echo "version number {$maj}.{$min}.{$mnt}" . PHP_EOL;
```
