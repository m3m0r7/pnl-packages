        # libsecp256k1 Package

        Package: `libsecp256k1/libsecp256k1`

        Base library: secp256k1

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsecp256k1
        ```

        The package requires secp256k1 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libsecp256k1\Libsecp256k1;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libsecp256k1 = $runtime->load(Libsecp256k1::class);

// Create a context for signing and verification, then destroy it.
// SECP256K1_CONTEXT_NONE = 1.
$ctx = $libsecp256k1->secp256k1_context_create(1);
$libsecp256k1->secp256k1_context_destroy($ctx);

// Explore further: secp256k1_ec_pubkey_create(), secp256k1_ecdsa_sign(),
// secp256k1_ecdsa_verify(), secp256k1_ec_seckey_verify(), ...
        ```

        This snippet is printed when `pnl install libsecp256k1` finishes — it comes from the package's `examples` field in `pnlx.json`.
