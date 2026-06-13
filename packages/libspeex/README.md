        # libspeex Package

        Package: `libspeex/libspeex`

        Base library: speex

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libspeex
        ```

        The package requires speex headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libspeex\Libspeex;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libspeex = $runtime->load(Libspeex::class);

// Create a narrowband encoder (SPEEX_MODEID_NB = 0) and free it.
$mode = $libspeex->speex_lib_get_mode(0);
$encoder = $libspeex->speex_encoder_init($mode);
$libspeex->speex_encoder_destroy($encoder);

// Explore further: speex_bits_init(), speex_encode_int(),
// speex_decoder_init(), speex_decode_int(), ...
        ```

        This snippet is printed when `pnl install libspeex` finishes — it comes from the package's `examples` field in `pnlx.json`.
