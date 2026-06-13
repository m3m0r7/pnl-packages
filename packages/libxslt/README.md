        # libxslt Package

        Package: `libxslt/libxslt`

        Base library: libxslt

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libxslt
        ```

        The package requires libxslt headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libxslt\Libxslt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libxslt = $runtime->load(Libxslt::class);

// Allocate an empty stylesheet and release it again.
$sheet = $libxslt->xsltNewStylesheet();
$libxslt->xsltFreeStylesheet($sheet);
$libxslt->xsltCleanupGlobals();

// Explore further: xsltParseStylesheetFile(), xsltApplyStylesheet(),
// xsltSaveResultToString(), xsltFreeStylesheet(), ...
        ```

        This snippet is printed when `pnl install libxslt` finishes — it comes from the package's `examples` field in `pnlx.json`.
