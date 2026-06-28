# libtasn1/libtasn1 error messages

Translate libtasn1 status codes into human-readable messages with `asn1_strerror()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtasn1\Libtasn1;

// asn1_strerror() maps a libtasn1 status code to a human-readable message.
// ASN1_SUCCESS=0, ASN1_ELEMENT_NOT_FOUND=2, ASN1_DER_ERROR=4.
foreach ([0, 2, 4] as $code) {
    echo $code . ': ' . (string) Libtasn1::asn1_strerror($code) . PHP_EOL;
}
```
