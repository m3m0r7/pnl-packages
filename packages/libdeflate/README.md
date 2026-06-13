        # libdeflate Package

        Package: `libdeflate/libdeflate`

        Base library: libdeflate

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libdeflate
        ```

        The package requires libdeflate headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libdeflate\Libdeflate;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libdeflate = $runtime->load(Libdeflate::class);

// Allocate a compressor at level 6, then free it.
$compressor = $libdeflate->libdeflate_alloc_compressor(6);
$libdeflate->libdeflate_free_compressor($compressor);

// Explore further: libdeflate_deflate_compress(), libdeflate_gzip_compress(),
// libdeflate_alloc_decompressor(), libdeflate_zlib_decompress(), ...
        ```

        This snippet is printed when `pnl install libdeflate` finishes — it comes from the package's `examples` field in `pnlx.json`.
