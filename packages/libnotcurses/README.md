        # libnotcurses Package

        Package: `libnotcurses/libnotcurses`

        Base library: notcurses

        License: Apache-2.0

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnotcurses
        ```

        The package requires notcurses headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libnotcurses\Libnotcurses;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnotcurses = $runtime->load(Libnotcurses::class);

// notcurses_version() returns the runtime version, e.g. "3.0.9".
$version = $libnotcurses->notcurses_version();
echo "notcurses: $version\n";

// Explore further: notcurses_core_init(), notcurses_stdplane(),
// ncplane_putstr(), notcurses_render(), notcurses_stop(), ...
        ```

        This snippet is printed when `pnl install libnotcurses` finishes — it comes from the package's `examples` field in `pnlx.json`.
