        # libwavpack Package

        Package: `libwavpack/libwavpack`

        Base library: wavpack

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libwavpack
        ```

        The package requires wavpack headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libwavpack\Libwavpack;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libwavpack = $runtime->load(Libwavpack::class);

// WavpackGetLibraryVersionString() returns the library version, e.g. "5.7.0".
$version = $libwavpack->WavpackGetLibraryVersionString();
echo "WavPack version: $version\n";

// Explore further: WavpackOpenFileInput(), WavpackUnpackSamples(),
// WavpackGetNumSamples(), WavpackGetSampleRate(), ...
        ```

        This snippet is printed when `pnl install libwavpack` finishes — it comes from the package's `examples` field in `pnlx.json`.
