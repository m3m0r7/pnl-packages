        # libgnutls Package

        Package: `libgnutls/libgnutls`

        Base library: GnuTLS

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libgnutls
        ```

        The package requires GnuTLS headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libgnutls\Libgnutls;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libgnutls = $runtime->load(Libgnutls::class);

// gnutls_check_version(null) returns the runtime version string.
$version = $libgnutls->gnutls_check_version(null);
echo "GnuTLS: $version\n";

// Explore further: gnutls_global_init(), gnutls_init(),
// gnutls_handshake(), gnutls_record_send(), ...
        ```

        This snippet is printed when `pnl install libgnutls` finishes — it comes from the package's `examples` field in `pnlx.json`.
