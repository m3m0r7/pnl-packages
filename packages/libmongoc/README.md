        # libmongoc Package

        Package: `libmongoc/libmongoc`

        Base library: libmongoc

        License: Apache-2.0

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmongoc
        ```

        The package requires libmongoc headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libmongoc\Libmongoc;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libmongoc = $runtime->load(Libmongoc::class);

// mongoc_init() must run once before any other driver call.
$libmongoc->mongoc_init();
$version = $libmongoc->mongoc_get_version();
echo "libmongoc: $version\n";
$libmongoc->mongoc_cleanup();

// Explore further: mongoc_client_new(), mongoc_client_get_collection(),
// mongoc_collection_insert_one(), mongoc_collection_find_with_opts(), ...
        ```

        This snippet is printed when `pnl install libmongoc` finishes — it comes from the package's `examples` field in `pnlx.json`.
