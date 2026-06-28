# libfido2/libfido2 — credential object lifecycle

Allocate a credential with `fido_cred_new()`, read its default scalar fields (`fido_cred_prot`, `fido_cred_pin_minlen`), then release it with `fido_cred_free()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfido2\Libfido2;

// fido_cred_new() allocates a fresh credential object; its scalar getters return
// the current (default) field values before anything is set: the credential
// protection policy (fido_cred_prot) and the enforced minimum PIN length
// (fido_cred_pin_minlen) are both 0 on a new object. fido_cred_free() releases it.
$cred = Libfido2::fido_cred_new();

$prot = Libfido2::fido_cred_prot($cred);
$minlen = Libfido2::fido_cred_pin_minlen($cred);

echo 'cred protection policy: ' . (is_object($prot) ? $prot->toInt() : $prot) . "\n";
echo 'cred min PIN length: ' . (is_object($minlen) ? $minlen->toInt() : $minlen) . "\n";

Libfido2::fido_cred_free($cred);
echo "credential freed." . PHP_EOL;
```
