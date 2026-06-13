        # libtheora Package

        Package: `libtheora/libtheora`

        Base library: theora

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libtheora
        ```

        The package requires theora headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libtheora\Libtheora;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libtheora = $runtime->load(Libtheora::class);

// th_version_string() returns the Theora release string.
$version = $libtheora->th_version_string();
echo "libtheora: $version\n";

// Explore further: th_decode_alloc(), th_decode_packetin(),
// th_encode_alloc(), th_encode_packetout(), ...
        ```

        This snippet is printed when `pnl install libtheora` finishes — it comes from the package's `examples` field in `pnlx.json`.
