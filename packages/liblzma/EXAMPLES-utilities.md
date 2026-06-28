# liblzma/liblzma checksum & sizing utilities

Use the standalone helpers: compute a CRC32 over a buffer, ask for the worst-case compressed size of an input, and read the machine's total physical memory.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblzma\Liblzma;

$data = 'Hello, liblzma!';
$crc = Liblzma::lzma_crc32($data, strlen($data), 0);
echo 'crc32: ' . (is_object($crc) ? $crc->toInt() : $crc) . PHP_EOL; // e.g. 2212810394

$bound = Liblzma::lzma_stream_buffer_bound(1024);
echo 'buffer bound for 1024 bytes: ' . (is_object($bound) ? $bound->toInt() : $bound) . PHP_EOL; // e.g. 1168

$mem = Liblzma::lzma_physmem();
echo 'physical memory bytes: ' . (is_object($mem) ? $mem->toInt() : $mem) . PHP_EOL;
```
