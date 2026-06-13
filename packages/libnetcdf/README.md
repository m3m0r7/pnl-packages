        # libnetcdf Package

        Package: `libnetcdf/libnetcdf`

        Base library: netcdf

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnetcdf
        ```

        The package requires netcdf headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libnetcdf\Libnetcdf;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnetcdf = $runtime->load(Libnetcdf::class);

// nc_inq_libvers() returns the netCDF library version string.
$version = $libnetcdf->nc_inq_libvers();
echo "netCDF: $version\n";

// Explore further: nc_open(), nc_inq_varid(),
// nc_get_var_double(), nc_close(), ...
        ```

        This snippet is printed when `pnl install libnetcdf` finishes — it comes from the package's `examples` field in `pnlx.json`.
