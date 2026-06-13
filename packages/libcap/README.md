        # libcap Package

        Package: `libcap/libcap`

        Base library: libcap

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libcap
        ```

        The package requires libcap headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libcap\Libcap;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libcap = $runtime->load(Libcap::class);

// cap_init() allocates an empty capability set; cap_free() releases it.
$caps = $libcap->cap_init();
$libcap->cap_free($caps);

// Explore further: cap_get_proc(), cap_set_flag(),
// cap_set_proc(), cap_to_text(), ...
        ```

        This snippet is printed when `pnl install libcap` finishes — it comes from the package's `examples` field in `pnlx.json`.
