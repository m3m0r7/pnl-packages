        # libhunspell Package

        Package: `libhunspell/libhunspell`

        Base library: hunspell

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libhunspell
        ```

        The package requires hunspell headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libhunspell\Libhunspell;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libhunspell = $runtime->load(Libhunspell::class);

// Create a Hunspell handle from an affix + dictionary pair, then free it.
$handle = $libhunspell->Hunspell_create('en_US.aff', 'en_US.dic');
$libhunspell->Hunspell_destroy($handle);

// Explore further: Hunspell_spell(), Hunspell_suggest(),
// Hunspell_analyze(), Hunspell_free_list(), ...
        ```

        This snippet is printed when `pnl install libhunspell` finishes — it comes from the package's `examples` field in `pnlx.json`.
