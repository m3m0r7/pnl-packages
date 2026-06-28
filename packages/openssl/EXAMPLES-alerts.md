# openssl/openssl alert string decoding

Decode a TLS alert wire value (level in the high byte, description in the low byte) into the short and long human-readable strings exposed by libssl.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Openssl\Openssl;

// A TLS alert wire value packs the alert level in the high byte and the
// alert description in the low byte. Here we decode a "fatal handshake
// failure" alert (level 2, description 40) into human-readable strings.
$alert = (2 << 8) | 40; // 552

$type     = (string) Openssl::SSL_alert_type_string($alert);
$typeLong = (string) Openssl::SSL_alert_type_string_long($alert);
$desc     = (string) Openssl::SSL_alert_desc_string($alert);
$descLong = (string) Openssl::SSL_alert_desc_string_long($alert);

echo "Alert value : {$alert}\n";
echo "Type        : {$type} ({$typeLong})\n";
echo "Description  : {$desc} ({$descLong})\n";
// Alert value : 552
// Type        : F (fatal)
// Description  : HF (handshake failure)
```
