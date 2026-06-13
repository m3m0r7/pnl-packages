        # libopenjp2 Package

        Package: `libopenjp2/libopenjp2`

        Base library: openjpeg

        License: BSD-2-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libopenjp2
        ```

        The package requires openjpeg headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libopenjp2\Libopenjp2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libopenjp2 = $runtime->load(Libopenjp2::class);

// opj_version() returns the OpenJPEG version string, e.g. "2.5.2".
$version = $libopenjp2->opj_version();
echo "OpenJPEG: $version\n";

// Explore further: opj_create_decompress(), opj_setup_decoder(),
// opj_read_header(), opj_decode(), ...
        ```

        This snippet is printed when `pnl install libopenjp2` finishes — it comes from the package's `examples` field in `pnlx.json`.
