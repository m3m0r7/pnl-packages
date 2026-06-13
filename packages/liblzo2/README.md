        # liblzo2 Package

        Package: `liblzo2/liblzo2`

        Base library: lzo2

        License: GPL-2.0-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liblzo2
        ```

        The package requires lzo2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Liblzo2\Liblzo2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$liblzo2 = $runtime->load(Liblzo2::class);

// lzo_version_string() returns the LZO release, e.g. "2.10".
$version = $liblzo2->lzo_version_string();
echo "LZO: $version\n";

// Explore further: lzo1x_1_compress(), lzo1x_decompress_safe(),
// lzo_adler32(), lzo_init(), ...
        ```

        This snippet is printed when `pnl install liblzo2` finishes — it comes from the package's `examples` field in `pnlx.json`.
