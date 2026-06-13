        # libvpx Package

        Package: `libvpx/libvpx`

        Base library: libvpx

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libvpx
        ```

        The package requires libvpx headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libvpx\Libvpx;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libvpx = $runtime->load(Libvpx::class);

// vpx_codec_version_str() returns the library version, e.g. "v1.14.1".
$version = $libvpx->vpx_codec_version_str();
echo "libvpx version: $version\n";

// vpx_codec_build_config() reports the compile-time configuration.
echo $libvpx->vpx_codec_build_config(), "\n";

// Explore further: vpx_codec_enc_init(), vpx_codec_encode(),
// vpx_codec_decode(), vpx_codec_get_frame(), ...
        ```

        This snippet is printed when `pnl install libvpx` finishes — it comes from the package's `examples` field in `pnlx.json`.
