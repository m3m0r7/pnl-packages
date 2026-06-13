        # libnlopt Package

        Package: `libnlopt/libnlopt`

        Base library: nlopt

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnlopt
        ```

        The package requires nlopt headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libnlopt\Libnlopt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnlopt = $runtime->load(Libnlopt::class);

// Create an optimizer over 2 variables (NLOPT_LD_MMA = 24), then free it.
$opt = $libnlopt->nlopt_create(24, 2);
$libnlopt->nlopt_destroy($opt);

// Explore further: nlopt_set_min_objective(), nlopt_set_xtol_rel(),
// nlopt_optimize(), nlopt_set_lower_bounds(), ...
        ```

        This snippet is printed when `pnl install libnlopt` finishes — it comes from the package's `examples` field in `pnlx.json`.
