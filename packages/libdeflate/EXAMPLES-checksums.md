# libdeflate/libdeflate Adler-32 and CRC-32 checksums

Besides (de)compression, libdeflate ships fast standalone checksum routines: `libdeflate_crc32()` and `libdeflate_adler32()` are pure transforms that take a running value plus a buffer and return the updated checksum.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libdeflate\Libdeflate;

// libdeflate ships fast Adler-32 and CRC-32 checksum routines (pure transforms).
$num = static fn($x) => is_object($x) ? $x->toInt() : $x;

$data = 'The quick brown fox jumps over the lazy dog';

// CRC-32 starts from 0; Adler-32 starts from 1.
$crc = $num(Libdeflate::libdeflate_crc32(0, $data, strlen($data)));
$adler = $num(Libdeflate::libdeflate_adler32(1, $data, strlen($data)));

printf("crc32   = 0x%08x\n", $crc);
printf("adler32 = 0x%08x\n", $adler);

// Cross-check CRC-32 against PHP's built-in crc32().
echo 'crc32 matches PHP crc32(): ' . ($crc === crc32($data) ? 'yes' : 'no') . PHP_EOL;
```
