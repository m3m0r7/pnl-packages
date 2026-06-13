# libsecp256k1/libsecp256k1 examples

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
