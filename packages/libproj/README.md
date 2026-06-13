        # libproj Package

        Package: `libproj/libproj`

        Base library: proj

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libproj
        ```

        The package requires proj headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libproj\Libproj;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libproj = $runtime->load(Libproj::class);

// proj_context_create() makes a threading context; free it when done.
$ctx = $libproj->proj_context_create();
$libproj->proj_context_destroy($ctx);

// Explore further: proj_create_crs_to_crs(), proj_trans(),
// proj_normalize_for_visualization(), proj_destroy(), ...
        ```

        This snippet is printed when `pnl install libproj` finishes — it comes from the package's `examples` field in `pnlx.json`.
