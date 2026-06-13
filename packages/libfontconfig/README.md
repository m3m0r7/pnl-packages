        # libfontconfig Package

        Package: `libfontconfig/libfontconfig`

        Base library: fontconfig

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libfontconfig
        ```

        The package requires fontconfig headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libfontconfig\Libfontconfig;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libfontconfig = $runtime->load(Libfontconfig::class);

// FcGetVersion() returns the runtime version, e.g. 21500 for 2.15.0.
$version = $libfontconfig->FcGetVersion();
echo "fontconfig version: $version\n";

// Initialise the default configuration.
$libfontconfig->FcInit();

// Explore further: FcConfigGetCurrent(), FcPatternCreate(),
// FcNameParse(), FcFontList(), FcFontMatch(), ...
        ```

        This snippet is printed when `pnl install libfontconfig` finishes — it comes from the package's `examples` field in `pnlx.json`.
