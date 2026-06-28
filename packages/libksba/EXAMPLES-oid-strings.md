# libksba string and OID helpers

Use libksba's standalone string utilities: copy a string through its allocator and decode the DER content octets of an OBJECT IDENTIFIER into dotted-decimal form.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libksba\Libksba;

// ksba_strdup() copies a C string through libksba's own allocator and hands
// the duplicate back, a handy round-trip that needs no parsing state.
$copy = Libksba::ksba_strdup('hello libksba');
echo 'strdup: ' . (string)$copy . "\n";

// ksba_oid_to_str() decodes the DER content octets of an OBJECT IDENTIFIER
// into its dotted-decimal form; 0x55 0x04 0x03 is the OID for commonName.
$der = "\x55\x04\x03";
$oid = Libksba::ksba_oid_to_str($der, strlen($der));
echo 'oid 2.5.4.3: ' . (string)$oid . "\n";
```
