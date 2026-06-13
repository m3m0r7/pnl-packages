        # libcbor Package

        Package: `libcbor/libcbor`

        Base library: libcbor

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libcbor
        ```

        The package requires libcbor headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libcbor\Libcbor;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libcbor = $runtime->load(Libcbor::class);

// Build a CBOR unsigned integer item.
$item = $libcbor->cbor_build_uint32(1234);
// ... serialise or inspect $item, then release it with cbor_decref().

// Explore further: cbor_load(), cbor_serialize_alloc(),
// cbor_new_definite_map(), cbor_map_add(), cbor_decref(), ...
        ```

        This snippet is printed when `pnl install libcbor` finishes — it comes from the package's `examples` field in `pnlx.json`.
