        # libnng Package

        Package: `libnng/libnng`

        Base library: nng

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnng
        ```

        The package requires nng headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libnng\Libnng;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnng = $runtime->load(Libnng::class);

// nng_version() returns the NNG version string, e.g. "1.8.0".
$version = $libnng->nng_version();
echo "nng: $version\n";

// Explore further: nng_req0_open(), nng_dial(),
// nng_send(), nng_recv(), nng_listen(), ...
        ```

        This snippet is printed when `pnl install libnng` finishes — it comes from the package's `examples` field in `pnlx.json`.
