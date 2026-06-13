        # libglib2 Package

        Package: `libglib2/libglib2`

        Base library: glib-2.0

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libglib2
        ```

        The package requires glib-2.0 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libglib2\Libglib2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libglib2 = $runtime->load(Libglib2::class);

// g_get_num_processors() returns the CPU count GLib sees.
$cpus = $libglib2->g_get_num_processors();
echo "GLib sees $cpus CPU(s)\n";

// Explore further: g_strdup(), g_hash_table_new(),
// g_list_append(), g_main_loop_new(), ...
        ```

        This snippet is printed when `pnl install libglib2` finishes — it comes from the package's `examples` field in `pnlx.json`.
