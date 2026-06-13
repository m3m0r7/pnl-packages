        # libconfig Package

        Package: `libconfig/libconfig`

        Base library: libconfig

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libconfig
        ```

        The package requires libconfig headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libconfig\Libconfig;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libconfig = $runtime->load(Libconfig::class);

// Initialise a config_t, read a file, then release it.
$cfg = FFI::new('config_t'); // allocate a config_t
$libconfig->config_init(FFI::addr($cfg));
// $libconfig->config_read_file(FFI::addr($cfg), 'app.cfg');
$libconfig->config_destroy(FFI::addr($cfg));

// Explore further: config_read_file(), config_lookup(),
// config_lookup_string(), config_setting_get_int(), ...
        ```

        This snippet is printed when `pnl install libconfig` finishes — it comes from the package's `examples` field in `pnlx.json`.
