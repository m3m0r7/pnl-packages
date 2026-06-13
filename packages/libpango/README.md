        # libpango Package

        Package: `libpango/libpango`

        Base library: pango

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libpango
        ```

        The package requires pango headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libpango\Libpango;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libpango = $runtime->load(Libpango::class);

// pango_version_string() returns the Pango version, e.g. "1.52.0".
$version = $libpango->pango_version_string();
echo "Pango: $version\n";

// Explore further: pango_font_description_new(), pango_layout_new(),
// pango_layout_set_text(), pango_cairo_show_layout(), ...
        ```

        This snippet is printed when `pnl install libpango` finishes — it comes from the package's `examples` field in `pnlx.json`.
