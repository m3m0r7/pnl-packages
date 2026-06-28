# libnetcdf error messages and type sizes

Translate netCDF status codes into messages with `nc_strerror()` and look up the byte width of an external data type with `nctypelen()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnetcdf\Libnetcdf;

// nc_strerror() maps a numeric netCDF status code to a human-readable message.
echo "status 0:   " . (string)Libnetcdf::nc_strerror(0) . "\n";
echo "status -33: " . (string)Libnetcdf::nc_strerror(-33) . "\n";

// nctypelen() returns the size in bytes of a netCDF external data type.
$intLen = Libnetcdf::nctypelen(4);    // NC_INT
$dblLen = Libnetcdf::nctypelen(6);    // NC_DOUBLE
echo "NC_INT bytes:    " . (is_object($intLen) ? $intLen->toInt() : $intLen) . "\n";
echo "NC_DOUBLE bytes: " . (is_object($dblLen) ? $dblLen->toInt() : $dblLen) . "\n";
```
