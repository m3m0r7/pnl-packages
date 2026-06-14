# libzip/libzip examples

```php
use Pnlx\Libzip\Libzip;
use function Pnlx\Util\is_null;

$libzip = new Libzip();

// zip_open() opens a ZIP archive; zip_get_num_entries() counts its entries.
$errp = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$zip = $libzip->zip_open("/path/to/archive.zip", 0, $errp);
if (is_null($zip)) {
    echo "zip_open failed, error: " . $errp[0] . "\n";
} else {
    $count = $libzip->zip_get_num_entries($zip, 0);
    echo "Entries: $count\n";
    $libzip->zip_close($zip);
}
```
