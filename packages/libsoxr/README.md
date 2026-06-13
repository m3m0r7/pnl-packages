        # libsoxr Package

        Package: `libsoxr/libsoxr`

        Base library: soxr

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsoxr
        ```

        The package requires soxr headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libsoxr\Libsoxr;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libsoxr = $runtime->load(Libsoxr::class);

// soxr_version() returns the libsoxr version string.
$version = $libsoxr->soxr_version();
echo "libsoxr: $version\n";

// Explore further: soxr_create(), soxr_process(),
// soxr_oneshot(), soxr_delete(), ...
        ```

        This snippet is printed when `pnl install libsoxr` finishes — it comes from the package's `examples` field in `pnlx.json`.
