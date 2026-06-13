        # libvterm Package

        Package: `libvterm/libvterm`

        Base library: vterm

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libvterm
        ```

        The package requires vterm headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libvterm\Libvterm;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libvterm = $runtime->load(Libvterm::class);

// Create an 80x24 virtual terminal, then free it.
$vt = $libvterm->vterm_new(24, 80);
$libvterm->vterm_free($vt);

// Explore further: vterm_obtain_screen(), vterm_input_write(),
// vterm_screen_get_cell(), vterm_screen_reset(), ...
        ```

        This snippet is printed when `pnl install libvterm` finishes — it comes from the package's `examples` field in `pnlx.json`.
