        # libmaxminddb Package

        Package: `libmaxminddb/libmaxminddb`

        Base library: libmaxminddb

        License: Apache-2.0

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmaxminddb
        ```

        The package requires libmaxminddb headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libmaxminddb\Libmaxminddb;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libmaxminddb = $runtime->load(Libmaxminddb::class);

// MMDB_lib_version() returns the libmaxminddb version string.
$version = $libmaxminddb->MMDB_lib_version();
echo "libmaxminddb: $version\n";

// Explore further: MMDB_open(), MMDB_lookup_string(),
// MMDB_get_value(), MMDB_close(), ...
        ```

        This snippet is printed when `pnl install libmaxminddb` finishes — it comes from the package's `examples` field in `pnlx.json`.
