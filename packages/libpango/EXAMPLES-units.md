# libpango version and unit conversions

`pango_version()` reports the runtime version as an integer, and the `pango_units_from_double()` / `pango_units_to_double()` pair converts between device units and Pango's fixed-point units (PANGO_SCALE = 1024).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpango\Libpango;

// pango_version() returns the runtime version encoded as an integer,
// e.g. 15200 for Pango 1.52.0.
$v = Libpango::pango_version();
echo (is_object($v) ? $v->toInt() : $v) . PHP_EOL;

// Pango measures distances in fixed-point "units" (PANGO_SCALE = 1024 per
// device unit). These helpers convert doubles to units and back.
$units = Libpango::pango_units_from_double(1.0);
$unitsInt = is_object($units) ? $units->toInt() : $units;
echo $unitsInt . PHP_EOL; // 1024

$back = Libpango::pango_units_to_double($unitsInt);
echo (is_object($back) ? $back->toFloat() : $back) . PHP_EOL; // 1
```
