        # libjxl Package

        Package: `libjxl/libjxl`

        Base library: libjxl

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libjxl
        ```

        The package requires libjxl headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libjxl\Libjxl;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libjxl = $runtime->load(Libjxl::class);

// JxlDecoderVersion() returns the encoded version, e.g. 10002 for 0.10.2.
$version = $libjxl->JxlDecoderVersion();
echo "libjxl version code: $version\n";

// Explore further: JxlDecoderCreate(), JxlDecoderProcessInput(),
// JxlEncoderCreate(), JxlEncoderAddImageFrame(), ...
        ```

        This snippet is printed when `pnl install libjxl` finishes — it comes from the package's `examples` field in `pnlx.json`.
