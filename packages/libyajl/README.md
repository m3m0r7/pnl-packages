        # libyajl Package

        Package: `libyajl/libyajl`

        Base library: yajl

        License: ISC

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libyajl
        ```

        The package requires yajl headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libyajl\Libyajl;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libyajl = $runtime->load(Libyajl::class);

// Build a tiny JSON document with the streaming generator.
$gen = $libyajl->yajl_gen_alloc(null);
$libyajl->yajl_gen_integer($gen, 42);
$libyajl->yajl_gen_free($gen);

// Explore further: yajl_alloc(), yajl_parse(), yajl_complete_parse(),
// yajl_gen_get_buf(), yajl_gen_map_open(), ...
        ```

        This snippet is printed when `pnl install libyajl` finishes — it comes from the package's `examples` field in `pnlx.json`.
