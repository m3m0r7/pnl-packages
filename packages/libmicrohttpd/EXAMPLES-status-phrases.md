# libmicrohttpd HTTP status phrases and binary version

Look up the standard reason phrase for HTTP status codes and read the packed binary version number, without starting a server.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmicrohttpd\Libmicrohttpd;

// Map HTTP status codes to their standard reason phrases.
foreach ([200, 404, 500] as $code) {
    $phrase = Libmicrohttpd::MHD_get_reason_phrase_for($code);
    echo $code . ' ' . (string)$phrase . PHP_EOL;
}

// Packed binary version number (0xMMNNPPPP) as a single unsigned int.
$bin = Libmicrohttpd::MHD_get_version_bin();
$bin = is_object($bin) ? $bin->toInt() : $bin;
echo 'version_bin: 0x' . dechex($bin) . PHP_EOL;
```
