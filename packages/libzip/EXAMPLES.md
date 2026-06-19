# libzip/libzip examples

```php
use Pnlx\Libzip\Libzip;
use function Pnlx\Util\is_null;

// zip_open() opens a ZIP archive; its int error code is an out-parameter, so
// pass a plain variable by reference.
$errp = 0;
$zip = Libzip::zip_open("/path/to/archive.zip", 0, $errp);
if (is_null($zip)) {
    echo "zip_open failed, error: {$errp}\n";
} else {
    $count = Libzip::zip_get_num_entries($zip, 0);
    echo "Entries: $count\n";
    Libzip::zip_close($zip);
}
```
