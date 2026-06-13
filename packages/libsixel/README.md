        # libsixel Package

        Package: `libsixel/libsixel`

        Base library: libsixel

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsixel
        ```

        The package requires libsixel headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libsixel\Libsixel;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libsixel = $runtime->load(Libsixel::class);

// Grab the built-in xterm 256-colour palette (SIXEL_BUILTIN_XTERM256 = 2).
$dither = $libsixel->sixel_dither_get(2);
$libsixel->sixel_dither_unref($dither);

// Explore further: sixel_encoder_new(), sixel_encoder_encode(),
// sixel_output_new(), sixel_dither_new(), sixel_encode(), ...
        ```

        This snippet is printed when `pnl install libsixel` finishes — it comes from the package's `examples` field in `pnlx.json`.
