        # libass Package

        Package: `libass/libass`

        Base library: libass

        License: ISC

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libass
        ```

        The package requires libass headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libass\Libass;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libass = $runtime->load(Libass::class);

// Create an ass_library handle, then free it.
$library = $libass->ass_library_init();
$libass->ass_library_done($library);

// Explore further: ass_renderer_init(), ass_new_track(),
// ass_read_file(), ass_render_frame(), ...
        ```

        This snippet is printed when `pnl install libass` finishes — it comes from the package's `examples` field in `pnlx.json`.
