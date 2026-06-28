# libserialport/libserialport version inspection

Query libserialport's package and library version numbers without opening any serial hardware.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libserialport\Libserialport;

// Query libserialport's build identity without opening any hardware. The package
// version functions return plain ints (wrapped as Int_, so normalise with toInt());
// the *_string helpers return the human-readable version strings.
$asInt = static fn ($v) => is_object($v) ? $v->toInt() : $v;

$major = $asInt(Libserialport::sp_get_major_package_version());
$minor = $asInt(Libserialport::sp_get_minor_package_version());
$micro = $asInt(Libserialport::sp_get_micro_package_version());
echo "Package version: {$major}.{$minor}.{$micro}\n";

echo 'Package version string: ' . (string) Libserialport::sp_get_package_version_string() . "\n";
echo 'Library version string: ' . (string) Libserialport::sp_get_lib_version_string() . "\n";
```
