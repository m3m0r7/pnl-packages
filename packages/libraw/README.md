        # libraw Package

        Package: `libraw/libraw`

        Base library: libraw

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libraw
        ```

        The package requires libraw headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libraw\Libraw;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libraw = $runtime->load(Libraw::class);

// libraw_init(0) creates a processing handle; libraw_close() frees it.
$handle = $libraw->libraw_init(0);
$libraw->libraw_close($handle);

// Explore further: libraw_open_file(), libraw_unpack(),
// libraw_dcraw_process(), libraw_dcraw_make_mem_image(), ...
        ```

        This snippet is printed when `pnl install libraw` finishes — it comes from the package's `examples` field in `pnlx.json`.
