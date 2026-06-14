# libnetcdf/libnetcdf examples

```php
use Pnlx\Libnetcdf\Libnetcdf;

// nc_inq_libvers() returns the netCDF library version string.
$version = Libnetcdf::nc_inq_libvers();
echo "netCDF: $version\n";

// Explore further: nc_open(), nc_inq_varid(),
// nc_get_var_double(), nc_close(), ...
```
