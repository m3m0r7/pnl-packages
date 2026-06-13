        # libpopt Package

        Package: `libpopt/libpopt`

        Base library: popt

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libpopt
        ```

        The package requires popt headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libpopt\Libpopt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libpopt = $runtime->load(Libpopt::class);

// poptStrerror() turns a popt error code into a readable message.
$message = $libpopt->poptStrerror(-10);
echo "popt: $message\n";

// Explore further: poptGetContext(), poptGetNextOpt(),
// poptGetArg(), poptFreeContext(), ...
        ```

        This snippet is printed when `pnl install libpopt` finishes — it comes from the package's `examples` field in `pnlx.json`.
