# libsecp256k1/libsecp256k1 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsecp256k1\Libsecp256k1;

// Create a context for signing and verification, then destroy it.
// SECP256K1_CONTEXT_NONE = 1.
$ctx = Libsecp256k1::secp256k1_context_create(1);
Libsecp256k1::secp256k1_context_destroy($ctx);

// Explore further: secp256k1_ec_pubkey_create(), secp256k1_ecdsa_sign(),
// secp256k1_ecdsa_verify(), secp256k1_ec_seckey_verify(), ...
```
