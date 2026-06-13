        # liburiparser Package

        Package: `liburiparser/liburiparser`

        Base library: uriparser

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liburiparser
        ```

        The package requires uriparser headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Liburiparser\Liburiparser;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$liburiparser = $runtime->load(Liburiparser::class);

// uriparser parses a URI string into its RFC 3986 components.
// The parser writes into a UriUriA struct you allocate with FFI.
//
// Explore further: uriParseSingleUriA(), uriFreeUriMembersA(),
// uriToStringA(), uriNormalizeSyntaxA(), uriDissectQueryMallocA(), ...
        ```

        This snippet is printed when `pnl install liburiparser` finishes — it comes from the package's `examples` field in `pnlx.json`.
